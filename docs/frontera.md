# Experimento de frontera entre repositorios

Claude Code declaró haber cargado los archivos `CLAUDE.md` de la carpeta padre `blog/` y de `blog-api`, pero no el de `blog-ai`; informó que tenía disponibles las skills `marcador-blog-api` y `marcador-blog-ai`, y añadió el campo `fragmentos_coincidentes` a `ResultadoBusqueda` utilizando un nombre en español.

El archivo `MARCADORES-blog-api.txt` registró cinco operaciones, incluida la edición de `blog-ai/app/esquemas.py`, mientras que `MARCADORES-blog-ai.txt` no se generó; por tanto, en esta ejecución se observó que el hook de `blog-api` registró la modificación realizada en el repositorio añadido, pero no se observó la ejecución del hook propio de `blog-ai`.
