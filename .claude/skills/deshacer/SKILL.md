---
name: deshacer
description: Volver atrás un cambio, ya sea uno en curso que Gael no quiere más o uno ya publicado en el sitio. Usar cuando Gael pide deshacer, volver atrás o sacar algo.
---

# Deshacer

Primero averiguá cuál de los dos casos es (preguntale a Gael si no está claro).

## A. Un cambio que todavía no se publicó

1. Mostrale en una línea qué se pierde.
2. Con su sí:
   - si tiene PR abierto: `gh pr close --delete-branch`;
   - después `git switch main && git pull` y, si la rama local sigue, `git branch -D <rama>`.

## B. Algo que ya está publicado

No se borra historia: se publica un cambio que lo revierte.

1. `git switch main && git pull`, y buscá el cambio con `git log --oneline -15` (cada publicación es un commit con el título del PR). Confirmale a Gael cuál vas a deshacer.
2. `git switch -c cambio/revert-<descripcion>` y `git revert <commit> --no-edit`.
3. Seguí con `/ver-preview` para que Gael confirme que quedó como antes, y después `/publicar`.

Si es urgente (el sitio está roto y no puede esperar el preview), decile a Gael que le pida a Joaquín volver a la versión anterior desde Cloudflare (es instantáneo) y armale el mensaje.
