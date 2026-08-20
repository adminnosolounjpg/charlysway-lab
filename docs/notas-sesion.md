# Masterclass: de HTML a URL en 15 minutos

Duración: 55 minutos. Formato: demostración corta y práctica larga.

**La regla que decide si la clase ha funcionado:** cada persona sale con una URL propia publicada. Si al final alguien no la tiene, la clase no ha servido, por bien que haya salido la demo.

## Antes de empezar (el día anterior)

- [ ] Todos con Claude Code instalado y funcionando. Esto se comprueba el día antes, no en clase.
- [ ] Cuenta del Lab creada y `CLOUDFLARE_ACCOUNT_ID` / `CLOUDFLARE_API_TOKEN` repartidos.
- [ ] Tú con dos pestañas abiertas: una pieza hecha sin la skill y otra con la skill, para el arranque.
- [ ] El encargo de práctica elegido y escrito en un sitio donde todos lo vean.

## Encargos de práctica (elige uno)

El mismo para todos, para poder comparar y ayudar rápido:

1. **Página de bienvenida** para alguien que entra nuevo al equipo: qué hace los primeros días y qué enlaces necesita.
2. **Guía de un proceso** que hoy se explica por WhatsApp veinte veces al mes.
3. **One-pager de una idea** para enseñarla en una reunión en vez de contarla.

El primero es el más seguro: todos entienden el encargo y nadie se atasca decidiendo qué hacer.

## Minutado

### 0-4 · La prueba del algodón

Dos páginas en pantalla, hechas con el mismo encargo: una "a pelo" y otra con la skill de marca. Sin explicar nada todavía.

Una sola frase: "las dos las ha hecho Claude en el mismo tiempo, la diferencia es que a la segunda le he dicho quiénes somos".

No expliques qué es una skill. Todavía no les importa.

### 4-8 · Instalación

Dos comandos, en directo, y que los escriban a la vez que tú:

```
/plugin marketplace add humberto-ui/charlysway-lab
/plugin install charlysway-web@charlysway
```

Reiniciar Claude Code y comprobar con `/cw-empezar` que aparece.

Si esto dura más de cuatro minutos, algo está mal preparado. Ten a mano el plan B: que se pongan con quien lo tenga funcionando y sigan mirando.

### 8-22 · Demo completa, de principio a fin

Un encargo real, del día a día. Enseña las cuatro fases sin saltarte ninguna:

1. **Pedir.** Un prompt normal, en lenguaje de persona. Enséñales que no hace falta invocar la skill: se activa sola.
2. **Revisar.** Abre lo que ha salido y léelo con ellos. Señala en voz alta qué está bien y qué no.
3. **Corregir.** Pide un cambio concreto, de una sola cosa. Este es el momento más importante de la clase.
4. **Publicar.** El comando, la URL, y abrirla en el navegador.

Durante la demo, provoca a propósito los tres tropiezos que van a tener sí o sí:

- **Las imágenes rotas en la vista previa.** Enséñaselo y explica que es la vista previa, no la página. Publica y demuestra que se ven bien. Si no lo ven aquí, te lo van a preguntar cinco veces.
- **Pedir un cambio en vez de volver a empezar.** El reflejo natural es reescribir el prompt entero. Enseña a decir "cambia solo el bloque de precios y deja el resto".
- **Lo que no se inventa.** Pon un dato que no tengas (una cifra, un testimonio) y enseña que se pregunta, no se rellena.

### 22-40 · Lo hacen ellos

Mismo encargo para todos, en parejas, 18 minutos de reloj.

Tú y quien te ayude circulando. No resuelvas tú el problema en su teclado: pregunta "¿qué le has pedido?" y deja que lo arreglen.

A los 12 minutos, aviso en voz alta: "quien no haya publicado todavía, que publique lo que tenga aunque esté a medias". Publicar a medias enseña más que terminar sin publicar.

Cierre del bloque: que cada pareja pegue su URL en el chat del equipo. Ahí se ve de un vistazo quién lo ha conseguido.

### 40-48 · Las reglas del carril

Están escritas en la portada del Lab, así que se leen desde ahí, en pantalla.

Insiste en dos:

- **Nada de datos de personas.** Ni leads, ni alumnos, ni capturas del CRM. El Lab no tiene aviso legal ni consentimiento.
- **Producción no se toca.** Si la pieza tiene que acabar en la web de verdad, se pasa a Tecnología. El Lab es para lo interno.

Y deja clara la frontera de "hasta aquí llegas tú": páginas internas, guías, one-pagers y maquetas para explicar una idea. Todo lo que lleve datos, formularios conectados o dominio público, no.

### 48-55 · Preguntas y cierre

Recuérdales que todo lo que has contado lo tienen dentro de Claude Code escribiendo `/cw-empezar`, así que no hay nada que memorizar ni ningún PDF que buscar.

Y cierra con una sola tarea: **que cada uno publique una pieza suya esta semana**. Una de verdad, de algo que necesite.

Sin esa tarea, en quince días nadie se acuerda de que esto existe.

## Después de la clase

- Pasa por el Lab a la semana y mira qué se ha publicado. Es la única métrica que importa.
- Lo que se atasque dos veces, va a la skill. Si dos personas tropiezan con lo mismo, no es culpa suya, es que falta una instrucción.

## Si algo sale mal en directo

| Problema | Qué haces |
|---|---|
| A alguien no le instala el plugin | Que siga en pareja. No pares la clase por una máquina |
| El deploy falla por credenciales | Comprueba las dos variables de entorno. Si no sale, que publique en tu máquina y siga |
| La pieza sale fea | No la arregles tú. Pregunta qué le pidió y enséñale a pedir el cambio |
| Alguien quiere publicar en la web real | Ahí se corta. Es la frontera, y es buen momento para explicar por qué existe |
| Vas justo de tiempo | Recorta la demo, nunca la práctica |
