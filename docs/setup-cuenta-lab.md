# Montar la cuenta del Lab

El Lab vive en una **cuenta de Cloudflare separada** de la del cliente. No es una carpeta aparte dentro de la cuenta de producción: es otra cuenta. Ese es el punto. Si el equipo tiene acceso a la cuenta donde vive `lp.charlysway.com`, cualquier error suyo llega a producción.

Coste: 0 €. Todo entra en el plan gratuito.

## 1. Crear la cuenta

Cuenta nueva de Cloudflare con un email de equipo (no el personal de nadie, para que no dependa de una persona). Algo tipo `lab@charlysway.com` o un alias.

Esa cuenta no tendrá dominios, ni DNS de producción, ni workers, ni bases de datos. Solo el proyecto Pages del Lab.

## 2. Crear el proyecto Pages

Desde el panel de la cuenta nueva: **Workers & Pages → Create → Pages → Upload assets**, con el nombre exacto **`cw-lab`**.

Sube cualquier cosa para el primer despliegue (vale la carpeta `sandbox/` de este repo). A partir de ahí el proyecto ya existe y todo se hace por línea de comandos.

La rama de producción del proyecto tiene que ser **`main`**. Es lo que hace que un deploy con `--branch=main` salga en el dominio y el resto queden como previews de cada persona.

## 3. Apuntar el subdominio

`lab.charlysway.com` es un subdominio del dominio del cliente, así que este paso lo tiene que hacer quien lleve el DNS de `charlysway.com` (Maitane o Ryan). Es un registro y nada más:

- En **Pages → cw-lab → Custom domains**, añadir `lab.charlysway.com`. Cloudflare dará un destino tipo `cw-lab.pages.dev`.
- En la zona DNS de `charlysway.com`, crear un **CNAME** `lab` → ese destino.

No toca ningún otro registro. No afecta al correo, ni a la web, ni a los funnels.

Mientras no esté el DNS, el Lab funciona igual en `https://cw-lab.pages.dev`. Se puede dar la clase con esa URL sin problema.

## 4. Cerrar el acceso

En **Zero Trust → Access → Applications**, protege `lab.charlysway.com` con una política de email: solo los correos `@charlysway.com` entran. Así el Lab no queda abierto a cualquiera que adivine la URL.

Es opcional para la clase, recomendable para el día a día.

## 5. Crear el token del equipo

En **My Profile → API Tokens → Create Token**, con permiso **Cloudflare Pages: Edit** sobre esta cuenta y nada más.

Ese token y el Account ID son lo que cada persona pone en su entorno:

```bash
export CLOUDFLARE_ACCOUNT_ID="<id de la cuenta lab>"
export CLOUDFLARE_API_TOKEN="<token>"
```

Como el token solo alcanza a esta cuenta, y esta cuenta solo contiene el Lab, lo peor que puede pasar con él es romper el Lab.

## 6. Comprobar que funciona

```bash
npx wrangler pages deploy sandbox --project-name=cw-lab --branch=main --commit-dirty=true
curl -sI https://lab.charlysway.com/ | head -5
curl -s https://lab.charlysway.com/ -o /dev/null -w "%{http_code}\n"
```

Comprueba también que la cabecera `x-robots-tag: noindex` está presente. La sirve el archivo `sandbox/_headers`.

## Lo que NO se hace en esta cuenta

- No se añade el dominio `charlysway.com` completo. Solo el subdominio como custom domain del proyecto.
- No se meten secretos, ni KV, ni Workers con credenciales.
- No se conecta a ActiveCampaign, ni a Meta, ni a Sly, ni a nada que reciba datos.
