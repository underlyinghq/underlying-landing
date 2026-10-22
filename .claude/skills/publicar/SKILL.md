---
name: publicar
description: Publicar en el sitio real el cambio que Gael ya vio en el preview (mergear el PR a main). Usar solo cuando Gael pide publicar.
---

# Publicar

1. Confirmá que hay un PR abierto para la rama actual (`gh pr view`). Si no hay, primero hacé `/ver-preview`: nunca se publica algo que Gael no vio.
2. Si hay cambios sin subir, subilos con el paso de `/ver-preview` y pasale el link nuevo a Gael antes de publicar. Lo que se publica tiene que ser exactamente lo que vio.
3. Verificá que los checks pasaron (`gh pr checks`). Si alguno falló, no publiques: explicale a Gael y arreglalo.
4. Mergeá: `gh pr merge --squash --delete-branch`.
5. `git switch main && git pull`.
6. Esperá uno o dos minutos y decile a Gael que ya está en el sitio real, con el link de producción (hoy `https://underlying-landing.pages.dev`; cuando se conecte el dominio, `https://underlyinghq.com`). Recordale que si algo quedó mal, `/deshacer` lo vuelve atrás.
