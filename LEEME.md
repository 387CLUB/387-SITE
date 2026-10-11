# Sitio de 387CLUB

## Qué hay en la carpeta

| Archivo | Para qué sirve |
|---|---|
| `index.html` | El sitio entero. Los datos de artistas, links y chistes del banner se editan arriba de todo, en el bloque `CONFIGURACIÓN`. |
| `videos.json` | Lista de videos de YouTube. La regenera sola el actualizador (ver más abajo). |
| `channels.json` | Los canales de YouTube que se miran (sello y artistas). |
| `scripts/update_videos.py` | Script que lee los canales y escribe `videos.json`. |
| `.github/workflows/update-videos.yml` | Hace que GitHub corra el script cada 6 horas. |
| `sprites/` | (la creás vos) los .gif de los artistas. |

## Cómo se actualizan los videos

**Sin hacer nada**, mientras `videos.json` esté vacío, el slider muestra un reproductor por canal con la lista de todo lo que ese canal sube. Cada video nuevo aparece solo.

**Con el actualizador** el slider muestra los últimos videos sueltos (uno por ventana, con su miniatura) y cada artista muestra sus 3 videos más recientes. Para activarlo:

1. Creá un repositorio en GitHub y subí **todo el contenido de esta carpeta** (incluida la carpeta oculta `.github`).
2. En el repositorio: Settings → Pages → elegí "Deploy from a branch" y la rama `main`.
3. En la pestaña Actions, abrí "Actualizar videos de YouTube" y apretá "Run workflow" para correrlo la primera vez.
4. Mirá el log de esa primera corrida: cada línea `[ok]` muestra el nombre del canal que encontró. Verificá que cada nombre sea el del artista correcto.

Desde ahí corre solo cada 6 horas y guarda los cambios en `videos.json`.

## Para agregar los .gif de los artistas

1. Creá una carpeta `sprites/` al lado de `index.html` y poné ahí los gifs (ej. `santoo.gif`).
2. En `index.html`, en cada artista, completá `sprite: "sprites/santoo.gif"`.
3. Conviene que tengan fondo transparente y miren hacia la derecha.
