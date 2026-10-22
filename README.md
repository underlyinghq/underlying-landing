# Landing de Underlying — guía para Gael

Con esto podés cambiar y publicar la landing vos solo, hablando con Claude Code. Claude se encarga de la parte técnica. Vos decidís qué cambiar y cuándo publicar.

## Cómo funciona, en una imagen

```
vos le pedís un cambio a Claude
        ↓
Claude lo hace y lo sube como "versión de prueba"  →  te da un link para verlo (celu, compu, pasárselo a alguien)
        ↓
si te gusta, le decís "publicalo"
        ↓
en 1–2 minutos está en el sitio real
```

Nada llega al sitio real sin que vos lo hayas visto antes y digas "publicalo". Si algo queda mal, se vuelve atrás.

## Instalación (una sola vez, mejor con Joaquín)

1. Instalar los programas:
   - **Windows** (en PowerShell):
     ```
     winget install Git.Git OpenJS.NodeJS.LTS GitHub.cli
     ```
   - **Mac** (con [Homebrew](https://brew.sh)):
     ```
     brew install git node gh
     ```
   Node tiene que ser la versión 24 o más nueva (`node -v` para verlo).
2. Entrar a GitHub con la cuenta de Underlying (`underlyinghq`):
   ```
   gh auth login
   gh auth setup-git
   ```
   Elegir GitHub.com → HTTPS → login con el navegador.
3. Bajar el proyecto y prepararlo:
   ```
   git clone https://github.com/underlyinghq/underlying-landing
   cd underlying-landing
   git config user.name "Gael"
   git config user.email "admin@underlyinghq.com"
   npm install
   ```
4. Abrir Claude Code en esa carpeta: `claude`.

## Uso diario

Abrí una terminal, andá a la carpeta (`cd underlying-landing`), escribí `claude` y pedile lo que quieras con tus palabras. También tenés estos atajos:

| Escribís | Qué hace |
|---|---|
| `/nuevo-cambio cambiar el título de la home` | Empieza un cambio nuevo |
| `/ver-preview` | Sube el cambio como versión de prueba y te da el link |
| `/publicar` | Lo pasa al sitio real (solo si ya lo viste) |
| `/deshacer` | Descarta un cambio en curso, o vuelve atrás algo ya publicado |

Consejos:
- Un tema por vez: termino o publico una cosa y después arranco la otra.
- Mirá siempre el link de prueba en el celular antes de publicar.
- Si pasás capturas o ejemplos de lo que querés, Claude lo hace más rápido y mejor.

## Cuándo llamar a Joaquín

- Si Claude te dice que algo falló y no lo puede arreglar: te va a armar un mensaje para mandarle.
- Si el sitio real se rompió y es urgente: Joaquín puede volver a la versión anterior en un minuto.
- Para dominios, formularios que guardan datos, o conectar la landing con la app.
