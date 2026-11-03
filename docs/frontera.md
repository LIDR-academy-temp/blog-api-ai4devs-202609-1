# Ejercicio Blog Polirepo — Frontera entre repositorios

## Frase 1 — Lo que declaró el agente

Claude Code indicó que al iniciar la sesión se cargaron los archivos CLAUDE.md de la carpeta padre blog/ y de blog-api/, mientras que el de blog-ai/ lo leyó posteriormente; declaró disponibles las skills marcador-blog-api y marcador-blog-ai, y eligió el nombre fragmentos_coincidentes para respetar la nomenclatura en español del contrato público.

## Frase 2 — Lo que demostraron los marcadores

MARCADORES-blog-api.txt registró la edición de blog-ai/app/esquemas.py mediante Edit, mientras que MARCADORES-blog-ai.txt no existía, lo que evidencia que en esta sesión se ejecutó el hook de blog-api, desde donde arrancó Claude Code, y no el hook del repositorio que contenía el archivo modificado.
