# Sitio de informes

Sitio estático con los informes del laboratorio, pensado para **GitHub Pages**.
No contiene modelos entrenados, pesos, datasets ni credenciales: sólo HTML,
imágenes y videos, para leer y mirar.

```
docs/
├── index.html                  portada, con la lista de informes
├── estilo.css                  hoja de estilo compartida por todos
├── .nojekyll                   que GitHub sirva los archivos tal cual
├── 01-laboratorio-ros2/
│   ├── index.html              el informe
│   ├── portada.jpg             miniatura para la portada
│   └── medios/                 7 imágenes + 6 videos (3,2 MB)
└── 02-rov-golfo-san-matias/
    ├── index.html
    ├── portada.jpg
    └── medios/                 6 imágenes + 2 videos (5,0 MB)
```

## Publicarlo

En el repositorio de GitHub, **Settings → Pages**, y elegir:

- **Source:** Deploy from a branch
- **Branch:** `main` · carpeta **`/docs`**

En un minuto queda en `https://<usuario>.github.io/<repositorio>/`.
No hace falta ninguna acción de build: son archivos estáticos.

## Verlo antes de publicar

```bash
python3 -m http.server 8899 --directory docs
```

Y abrir <http://127.0.0.1:8899/>. Conviene mirarlo así y no abriendo el archivo
con doble clic: `file://` no resuelve igual las rutas relativas de los videos.

## Agregar un informe

1. Crear `docs/03-lo-que-sea/` con su `index.html` y su carpeta `medios/`.
2. Enlazar `../estilo.css` desde el `<head>` para que herede el diseño.
3. Agregar una tarjeta `<a class="informe" href="03-lo-que-sea/">` en
   `docs/index.html`, copiando una de las que ya están. Van en orden
   inverso: el más reciente arriba.

El informe 01 se generó a partir de la bitácora, que lleva las figuras
empotradas en base64 porque tiene que ser autocontenida. Acá los medios van
sueltos: la página baja 26 KB de HTML y pide cada video sólo si alguien lo
reproduce, en lugar de 4,4 MB de entrada.
