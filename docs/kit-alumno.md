# Kit del alumno

Todo lo que necesitas para hacer una página tú solo. Guárdate esta página.

## 1. Instalar (una vez)

En Claude Code:

```
/plugin marketplace add humberto-ui/charlysway-lab
/plugin install charlysway-web@charlysway
```

Reinicia y escribe `/cw-marca` para comprobar que está.

## 2. Publicar

Tu pieza va en su propia carpeta dentro de `sandbox/`, y el nombre de la carpeta es la dirección.

```bash
npx wrangler pages deploy sandbox --project-name=cw-lab --branch=<tu-nombre> --commit-dirty=true
```

Eso te da tu URL. Cuando la pieza esté terminada y quieras que salga en el Lab de verdad, cambia `--branch=<tu-nombre>` por `--branch=main`.

## 3. Cinco prompts que puedes copiar

**Empezar una pieza**

> Hazme una página interna para [quién] que explique [qué]. Tiene que tener [las secciones que quieras]. Es para uso interno del equipo.

**Pedir un cambio concreto** (esto es lo que más vas a usar)

> Cambia solo [la parte]. Deja el resto igual.

**Cuando algo no te convence pero no sabes qué es**

> Revisa esta página contra la marca y dime qué está fuera de sitio, sin cambiar nada todavía.

**Cuando falta información**

> Para esta sección necesito [el dato]. No lo tengo. Deja un hueco marcado y sigue con el resto.

**Antes de publicar**

> Pásale el checklist de marca y dime si hay algo que no cumple.

## 4. Tres encargos para practicar

Empieza por el primero. Si te sobra tiempo, sigue.

1. **Página de bienvenida** para alguien que entra nuevo al equipo: qué hace los primeros días y qué enlaces necesita.
2. **Guía de un proceso** que hoy explicas por WhatsApp veinte veces al mes. El que se te venga a la cabeza ahora es el bueno.
3. **One-pager de una idea** que quieras proponer, para enseñarla en una reunión en vez de contarla.

## 5. Lo que va a pasarte

**Las imágenes salen rotas en la vista previa.** No está mal la página. La vista previa del chat bloquea las imágenes de fuera por seguridad. Publica y ábrela: se ven bien.

**Te va a apetecer reescribir el prompt entero.** No lo hagas. Pide el cambio de una cosa concreta y deja el resto quieto.

**Te va a inventar un dato si se lo dejas.** Cifras, testimonios, fechas y precios se preguntan. Si no lo tienes, se queda el hueco.

**La primera versión casi nunca es la buena.** Es normal, y arreglarla cuesta un minuto. Esa es la gracia.

## 6. Dónde está la frontera

**Puedes:** páginas internas, guías, one-pagers, índices de recursos, maquetas para explicar una idea.

**No puedes:** subir datos de personas (leads, alumnos, emails, teléfonos, capturas del CRM), conectar formularios que envíen información, meter claves o contraseñas, publicar cifras de facturación o cualquier cosa confidencial, ni tocar las webs de producción.

Si la pieza tiene que acabar en la web real, se pasa a Tecnología. El Lab es para lo interno.

**Y una cosa más:** el Lab no sale en Google, pero cualquiera con el enlace entra. Si no lo pondrías en una pizarra de la oficina, no lo subas.

## 7. Si te atascas

| Te pasa esto | Haz esto |
|---|---|
| No aparece `/cw-marca` | Reinicia Claude Code. Si sigue sin salir, repite los dos comandos de instalación |
| El deploy dice error de autenticación | Te faltan las dos variables de entorno del Lab, o son de otra cuenta |
| Publica pero la URL da 404 | Tu archivo tiene que llamarse `index.html` y estar dentro de `sandbox/tu-carpeta/` |
| Se ve sin estilos | Rutas rotas. Pide que use las URLs oficiales de los assets |
| Sale la versión antigua | Recarga con Ctrl+F5 |
