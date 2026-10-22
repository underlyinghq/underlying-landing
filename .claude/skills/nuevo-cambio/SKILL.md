---
name: nuevo-cambio
description: Empezar un cambio nuevo en la landing (texto, sección, diseño). Usar cuando Gael pide modificar algo y no hay un cambio en curso para eso.
---

# Nuevo cambio

Lo que Gael quiere cambiar: $ARGUMENTS (si está vacío, preguntale qué quiere cambiar).

1. `git status`. Si hay cambios sin guardar o estás en otra rama `cambio/...` con trabajo pendiente, contale a Gael y preguntale si lo terminamos primero, lo dejamos guardado en su rama o lo descartamos. No descartes nada sin que diga que sí.
2. `git switch main && git pull`.
3. `git switch -c cambio/<descripcion-corta-en-ingles>`.
4. Hacé el cambio. Si es grande, decile a Gael en dos líneas qué vas a tocar antes de empezar.
5. Corré `npm run build` y arreglá lo que falle.
6. Contale qué cambiaste en lenguaje simple y ofrecé dos caminos:
   - verlo ya en su compu (`npm run dev` en segundo plano, link http://localhost:4321), o
   - subirlo para tener el link de prueba que puede abrir en el celular o pasarle a otro (`/ver-preview`).

Si Gael sigue pidiendo ajustes sobre lo mismo, seguí en esta rama.
