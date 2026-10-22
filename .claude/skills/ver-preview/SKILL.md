---
name: ver-preview
description: Subir el cambio en curso y darle a Gael el link de la versión de prueba (preview de Cloudflare). Usar cuando Gael quiere ver o compartir cómo queda, sin publicar.
---

# Ver el preview

1. Confirmá que estás en una rama `cambio/...` (nunca en `main`). Si estás en `main` con cambios, creá la rama ahora: `git switch -c cambio/<descripcion>`.
2. `npm run build`. Si falla, arreglalo antes de seguir.
3. `git add -A`, revisá con `git status` que no entre nada raro (archivos `.env`, carpetas `dist/` o `node_modules/`), y commiteá con un mensaje corto en inglés.
4. `git push -u origin HEAD`.
5. Si la rama no tiene PR (`gh pr view` falla), creá uno contra `main`:
   `gh pr create --base main --title "<título corto en inglés>" --body "<qué cambia, en castellano simple, en 2-4 líneas>"`
6. Esperá a que Cloudflare termine (`gh pr checks --watch`, uno o dos minutos).
7. Buscá el link del preview en el comentario de Cloudflare del PR (`gh pr view --comments`) o en el detalle del check de Cloudflare (`gh pr checks`). Si no aparece en ninguno de los dos, no lo inventes: decile a Gael que el preview está listo pero no encontrás el link, y armale el mensaje para Joaquín.
8. Pasale a Gael el link y decile: "Esto todavía **no** está publicado. Si te gusta, decime 'publicalo'; si no, decime qué cambiar."

Si el check de Cloudflare falla, mirá el detalle (`gh pr checks`), arreglá si es un error del código y volvé a subir. Si no entendés el error, armá el mensaje para Joaquín.
