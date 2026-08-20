# Cómo es Charly's Way en digital, medido sobre las webs reales

Análisis hecho el 20 de agosto de 2026 sobre las cuatro propiedades vivas de la marca. Sirve para dos cosas: saber a qué te tienes que parecer, y saber dónde el manual y la realidad no coinciden.

## Las cuatro propiedades

| Web | Qué es | Con qué está hecha |
|---|---|---|
| `charlysway.com` | Web principal de la marca | WordPress + Bricks |
| `metodo.charlysway.com` | Gemela de la principal, para el método y sus funnels | WordPress + Bricks |
| `charlyswayacademy.com` | Academy: landings de Google Ads y páginas de curso | WordPress + Bricks |
| `lp.charlysway.com` | Funnels nuevos en código (registro, masterclass, replay, gracias) | HTML + Vite + Cloudflare Pages |

Las landings de `lp.` son lo más reciente y lo mejor mantenido. Cuando dudes de cómo se ve algo hoy, mira ahí.

## Color: lo que usan de verdad

Contando apariciones en el CSS publicado:

| Color | Valor real en las webs | Valor en el manual |
|---|---|---|
| Azul Charly | **`#098cb6`** (43 usos en las landings, 6 en la web principal) | `#0B89B0` |
| Naranja Charly | **`#f8774d`** (30 usos) | `#F47149` |
| Azul oscuro | `#122d44` (landings) · `#094e6c` (web principal, 16 usos) | `#243156` |
| Cuerpo de texto | `#0a0a0a` con secundario `#475569` | `#243156` |
| Fondo de tarjeta | `#eef4f8` (landings) · `#eaeef4` (web principal) | `#EDF1F8` |

El azul del manual aparece solo 2 veces en toda la web principal. **En digital manda `#098cb6`.** La diferencia con `#0B89B0` es imperceptible a ojo, pero si vas a mezclar tu pieza con capturas o secciones de la web, usa el de la web.

## Tipografía: zanjado

En el CSS de la web principal: **Poppins 39 usos, Antonio 14, Lato 2**. Las landings sirven sus propias `woff2` y solo hay dos familias en la carpeta: Antonio (400-700) y Poppins (300-800).

Aparece un `Inter` como fuente por defecto del tema Bricks, pero no lo usa ninguna pieza de marca. Ignóralo.

Conclusión: **Antonio para titulares, Poppins para todo lo demás**. El brand kit dice Lato porque se actualizó pensando en el manual impreso, y esa decisión no se trasladó a web a propósito.

## Formas: donde el manual y la web no coinciden

Las landings actuales tienen **119 `box-shadow`** y radios variados (999px para píldoras, 14/16/18px para cajas). El manual prohíbe las sombras y fija radio 8 en botones y 24 en tarjetas.

Manda el manual, porque la regla de "sin sombras, separar con borde fino" es posterior a esas landings y es lo que se está aplicando de aquí en adelante. Si abres una landing vieja y ves sombras, es deuda pendiente, no un ejemplo a copiar.

## Patrones que sí se repiten en toda la marca

Esto es el lenguaje visual real de CW, y conviene reproducirlo:

- **Cabecera blanca sólida** con el logo a la izquierda y un CTA a la derecha.
- **Hero sobre el fondo azul texturizado** con la línea del camino, titular Antonio gigante en mayúsculas y una frase corta de apoyo.
- **Badge o etiqueta encima del titular**, en Poppins Bold mayúsculas. Nunca en Antonio.
- **Pegatina de Charly recortada anclada al borde inferior**, contra el suelo de la composición.
- **CTAs naranjas rectangulares en mayúsculas**, siempre con verbo.
- **Tarjetas en azul muy claro** con esquinas generosas para bloques de programa o beneficios.
- **La línea discontinua del camino** cruzando fondos claros y oscuros como hilo conductor.

## Detalles útiles si tocas algo que ya existe

- Las landings de Google Ads de la academy son páginas duplicadas, cada una con su copia del contenido. No hay plantilla compartida: cambiar una no cambia las demás.
- La academy tiene carga diferida agresiva. El contenido de abajo no aparece en el HTML crudo ni en capturas automáticas, aunque un visitante real sí lo ve.
- La cifra de alumnos que aparece en las landings ("más de 22.000") está más actualizada que la de los documentos internos. Si ves una cifra distinta en un PDF viejo, pregunta antes de "corregir".
