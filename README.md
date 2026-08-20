# Charly's Way — skill de marca + El Lab

Dos cosas viven en este repo:

1. **La skill de marca** (`plugins/charlysway-web/`), que hace que Claude Code construya piezas web con la identidad de Charly's Way sin que tengas que explicarle nada.
2. **El Lab** (`sandbox/`), el entorno de pruebas donde el equipo publica sus piezas, en `lab.charlysway.com`.

## Instalar la skill

Dentro de Claude Code, dos comandos:

```
/plugin marketplace add humberto-ui/charlysway-lab
/plugin install charlysway-web@charlysway
```

Reinicia Claude Code y ya está. Comprueba que funciona escribiendo `/cw-marca`.

No hace falta cuenta de GitHub ni configurar nada: el repo es público y se descarga solo.

> **Este repo es público y no contiene credenciales.** Las claves del Lab viven en variables de entorno de cada persona, nunca aquí. Si alguna vez tienes que pegar un token en un archivo, ese archivo no va al repo.

## Qué te da

| Skill | Para qué |
|---|---|
| `/charlysway-web:cw-marca` | Construir o revisar cualquier pieza con la marca puesta: colores, tipografías, componentes, voz |
| `/charlysway-web:cw-publicar` | Publicar la pieza en el Lab y obtener su URL |

No hace falta invocarlas a mano. Si le pides a Claude "hazme una página de bienvenida para el equipo", carga la de marca sola.

## Publicar una pieza

Cada pieza vive en su carpeta dentro de `sandbox/`, y el nombre de la carpeta es la dirección:

```
sandbox/bienvenida-equipo/index.html  →  lab.charlysway.com/bienvenida-equipo/
```

Necesitas las credenciales del Lab en tu entorno (nunca las de producción):

```bash
export CLOUDFLARE_ACCOUNT_ID="<id de la cuenta lab>"
export CLOUDFLARE_API_TOKEN="<token de la cuenta lab>"
```

Mientras practicas, publica en tu propia rama para no pisar a nadie:

```bash
npx wrangler pages deploy sandbox --project-name=cw-lab --branch=<tu-nombre> --commit-dirty=true
```

Cuando la pieza está terminada y quieres que salga en `lab.charlysway.com`:

```bash
npx wrangler pages deploy sandbox --project-name=cw-lab --branch=main --commit-dirty=true
```

## Reglas del Lab

- Nada de datos de personas: leads, alumnos, emails, teléfonos, capturas del CRM.
- Nada de formularios conectados, claves ni información confidencial.
- Producción (`charlysway.com`, la academy, el método y `lp.charlysway.com`) no se toca desde aquí. Eso pasa siempre por Tecnología.
- El Lab lleva `noindex`, pero cualquiera con el link entra. Trátalo como semipúblico.

## Estructura

```
.claude-plugin/marketplace.json      catálogo para /plugin marketplace add
plugins/charlysway-web/
  .claude-plugin/plugin.json
  skills/cw-marca/SKILL.md           identidad de marca
    references/tokens.css            colores, tipos y escala listos para pegar
    references/plantilla.html        página de arranque completa
    references/componentes.md        hero, cards, CTAs, FAQ, formularios
    references/assets.md             URLs oficiales de logos y fondos
    references/webs-reales.md        cómo es CW en digital, medido sobre las webs
  skills/cw-publicar/SKILL.md        publicar en el Lab
sandbox/                             lo que se publica en lab.charlysway.com
  index.html                         portada del Lab con las reglas
  bienvenida-equipo/index.html       pieza de ejemplo
docs/setup-cuenta-lab.md             cómo se montó la cuenta y el subdominio
```

## Decisiones de marca que conviene conocer

- **La fuente de cuerpo es Poppins**, no Lato. El brand kit dice Lato porque aplica al manual impreso; todo lo publicado está en Poppins.
- **El azul es `#0B89B0` y el naranja `#F47149`**, los del manual y el campus. Las landings públicas usan un matiz ligeramente distinto (`#098cb6` / `#f8774d`), que es deriva histórica.
- **En texto pequeño, el azul va en `#086A8A`.** El azul de marca sobre blanco no llega al mínimo de contraste por debajo de 18px.
- **Sin sombras.** Las landings antiguas tienen, pero es deuda pendiente, no un ejemplo a seguir.
- **El campus tiene su propio design system.** Para maquetar dentro de la plataforma manda ese documento, no esta skill.

El detalle está en `plugins/charlysway-web/skills/cw-marca/references/webs-reales.md`.
