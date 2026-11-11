# Frontera

1. Arrancando la sesión en blog-api con `claude --add-dir ../blog-ai`, el agente dijo haber cargado solo dos CLAUDE.md, el de la carpeta `blog/` (REGLA-PADRE) y el de blog-api; listó como disponibles las skills `marcador-blog-api` y `marcador-blog-ai`, y llamó al campo `fragmentos_coincidentes`, en español, porque leyó por iniciativa propia el CLAUDE.md de blog-ai, que no se le había cargado.

2. El marcador de blog-api registró la edición de `/Users/brenda/blog/blog-ai/app/esquemas.py` y el marcador de blog-ai no existe: se ejecutó el guardarraíl del repositorio desde el que arranqué la sesión, no el del repositorio dueño del archivo, y el de blog-ai nunca corrió, y nada lo advirtió.
