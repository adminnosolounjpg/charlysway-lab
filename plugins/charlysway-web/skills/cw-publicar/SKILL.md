---
name: cw-publicar
description: Publica una pieza HTML de Charly's Way en el entorno de pruebas lab.charlysway.com y devuelve la URL. Úsala cuando haya que subir, publicar, desplegar o "poner online" una página del equipo, o cuando alguien pida ver su pieza en una URL real en vez de en la vista previa.
---

# Publicar en el lab

El lab (`lab.charlysway.com`) es el entorno de pruebas del equipo. Está en una cuenta de Cloudflare separada de todo lo de producción, así que aquí no se puede romper nada importante. Es el sitio donde practicar y donde alojar piezas internas del día a día.

## Antes de publicar

1. Pasa el checklist de marca de la skill `cw-marca`. Una pieza fuera de marca no se publica.
2. Comprueba las reglas del carril, abajo. Si la pieza incumple una, **no la publiques y dilo**.
3. La pieza debe ser un `index.html` autocontenido dentro de su propia carpeta.

## Estructura

Cada pieza vive en su carpeta, y el nombre de la carpeta es la URL:

```
sandbox/
  bienvenida-equipo/index.html   →  lab.charlysway.com/bienvenida-equipo/
  guia-onboarding/index.html     →  lab.charlysway.com/guia-onboarding/
```

Nombres de carpeta en minúsculas, con guiones, sin acentos ni espacios.

## Publicar

Las credenciales del lab viven en el archivo `.env` de la raíz del proyecto, que está fuera de git. Wrangler las lee solo con pasarle `--env-file=.env`, así que no hay que exportar nada.

Si el archivo no existe, cópialo de `.env.example` y pide las credenciales. **Nunca uses credenciales de producción aquí.**

**Para practicar o iterar** (cada persona tiene su propia URL y no pisa a nadie):

```bash
npx wrangler pages deploy sandbox --project-name=cw-lab --branch=<tu-nombre> --commit-dirty=true --env-file=.env
```

Eso devuelve una URL propia del tipo `https://<tu-nombre>.cw-lab.pages.dev`.

**Para dejar la pieza publicada de verdad en el lab**, cuando ya está terminada:

```bash
npx wrangler pages deploy sandbox --project-name=cw-lab --branch=main --commit-dirty=true --env-file=.env
```

Esa sí sale en `https://lab.charlysway.com/<carpeta>/`.

Después de publicar, **abre la URL y compruébala** antes de darla por buena. La vista previa del chat no cuenta: ahí las imágenes externas salen rotas siempre.

## Reglas del carril

Innegociables. Si una pieza las incumple, no se publica:

1. **Nada de datos de personas.** Ni leads, ni listas de alumnos, ni emails, ni teléfonos, ni capturas del CRM. El lab no tiene consentimiento ni aviso legal.
2. **Ningún formulario que envíe datos a algún sitio.** Maquetar un formulario está bien, conectarlo no.
3. **Nada de credenciales, tokens ni claves** dentro del HTML.
4. **Nada confidencial:** cifras de facturación, contratos, datos de clientes.
5. **No se toca producción.** `charlysway.com`, `charlyswayacademy.com`, `metodo.charlysway.com` y `lp.charlysway.com` no se despliegan desde aquí, jamás. Si la pieza tiene que acabar en una de esas, pásala a Tecnología.
6. El lab lleva `noindex`: no lo va a encontrar Google, pero **cualquiera con el link puede verlo**. Trátalo como semipúblico.

## Si algo falla

| Síntoma | Qué pasa |
|---|---|
| `Authentication error` o `code: 10000` | El token no es válido o es de otra cuenta. Comprueba las dos variables de entorno |
| `Project not found` | El nombre del proyecto no es `cw-lab`, o el token no tiene permiso sobre él |
| Publica pero la URL da 404 | La pieza no está en `sandbox/<carpeta>/index.html`, o el archivo no se llama `index.html` |
| La URL sale bien pero sin estilos ni imágenes | Rutas relativas rotas. Usa las URLs absolutas de los assets oficiales |
| Sale la versión vieja | Recarga saltando caché (Ctrl+F5). Si sigue, comprueba que desplegaste la rama correcta |

Nunca resuelvas un problema de permisos usando credenciales de producción. Si el token del lab no funciona, se pide uno nuevo del lab.
