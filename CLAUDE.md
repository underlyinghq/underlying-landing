# Landing de Underlying

## Con quién trabajás

Trabajás con **Gael**, socio de Underlying. Gael sabe de finanzas y de producto, **no es técnico**. Joaquín (el desarrollador) no está en el día a día de este repo: la idea es que Gael pueda cambiar y publicar la landing solo.

Cómo hablarle:
- Español rioplatense (vos), frases cortas, sin jerga. No digas "rama", "PR" o "merge" sin explicar en la misma frase qué significa para él ("lo dejé en una versión de prueba, todavía no está publicado").
- Antes de hacer algo, decile en una o dos líneas qué vas a hacer. Después, qué cambió y qué tiene que mirar.
- Si un pedido es ambiguo en lo visual (colores, textos, orden de secciones), proponé una opción concreta y hacela; no le hagas elegir entre cinco.
- Cuando algo falla y no lo podés resolver con seguridad, pará y dale un mensaje listo para mandarle a Joaquín (qué querías hacer, qué comando falló, el error).

## Qué es este repo

La landing pública de Underlying (va a vivir en `underlyinghq.com`; la app pasa a `app.underlyinghq.com`). Es un sitio **estático** hecho con [Astro](https://docs.astro.build):

- `src/pages/` — cada archivo es una página (`index.astro` es la home).
- `src/layouts/Base.astro` — el `<head>` y la estructura común.
- `src/components/` — piezas reutilizables (crear la carpeta cuando haga falta).
- `public/` — archivos que se sirven tal cual (favicon, imágenes, `robots.txt`).

Ver en la compu: `npm run dev` y abrir http://localhost:4321. Chequeo antes de subir: `npm run build`.

Los textos del sitio van en **inglés** salvo que Gael pida otra cosa. Mensajes de commit en inglés, cortos.

## Cómo se publica

Cloudflare (Workers con archivos estáticos, configurado en `wrangler.jsonc`) está conectado a este repo de GitHub:
- **Cualquier rama que se sube** genera una versión de prueba con su propio link (el preview). No la ve nadie que no tenga el link.
- **Lo que entra a `main` se publica** en el sitio real en uno o dos minutos.

Por eso el circuito es siempre: rama nueva → cambios → subir la rama y abrir un PR → Gael mira el preview → recién cuando Gael lo pide, se mergea a `main`.

Los comandos `/nuevo-cambio`, `/ver-preview`, `/publicar` y `/deshacer` hacen cada paso. Si Gael pide lo mismo con otras palabras ("publicalo", "quiero verlo", "volvé atrás"), seguí el comando que corresponde.

## Reglas que no se rompen

1. **Nunca commitear ni pushear directo a `main`.** Todo entra por un PR.
2. **Nunca `git push --force`, `git reset --hard` sobre trabajo subido, ni reescribir historia.** Para deshacer algo publicado se hace un revert (ver `/deshacer`).
3. **Mergear a `main` solo cuando Gael lo pide explícitamente** y después de que vio el preview.
4. **`npm run build` tiene que pasar antes de cada push.** Si falla, arreglarlo antes de subir.
5. **Nada secreto en el repo.** Es un sitio estático: todo lo que está acá lo puede ver cualquiera. Ni keys, ni contraseñas, ni emails privados, ni datos que no estén listos para ser públicos.
6. **No agregar dependencias** (`npm install <algo>`) sin explicarle a Gael para qué y que diga que sí. Preferir HTML y CSS a librerías.
7. **No tocar lo que no es de este repo:** configuración de Cloudflare (incluido `wrangler.jsonc`), DNS, settings del repo en GitHub, GitHub Actions, ni la app de Underlying (`underlying-app`).
8. **Una sola cuenta de GitHub: `underlyinghq`.** Si `gh auth status` muestra otra, parar y avisar.

## Cómo trabajar

- Al arrancar una sesión: `git status`. Si hay cambios sin guardar o una rama a medias, contale a Gael en qué estaba y preguntale si sigue con eso.
- Rama nueva siempre desde `main` actualizado (`git switch main && git pull`). Nombre: `cambio/<descripcion-corta-en-ingles>` (ej. `cambio/pricing-section`).
- Un PR por tema. Si Gael pide algo que no tiene que ver con el PR abierto, preguntale si lo sumás ahí o va aparte (recomendá aparte si es independiente).
- Todo tiene que verse bien en el celular: probá anchos chicos (375 px) además de escritorio.
- Imágenes: livianas (WebP o SVG cuando se pueda), con `alt` descriptivo.
- Si hay conflictos con `main` y no son triviales, avisá a Gael y armá el mensaje para Joaquín en vez de resolverlos a ciegas.
