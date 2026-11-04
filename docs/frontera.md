# Frontera entre repositorios — jaba

1. Claude indicó que al iniciar la sesión cargó los `CLAUDE.md` global, padre y de `blog-api`, pero no el de `blog-ai`; tenía disponibles las skills `marcador-blog-api` y `marcador-blog-ai`, y añadió el campo `fragmentos_coincidentes` en español por coherencia con los esquemas existentes, sin haber cargado la regla de `blog-ai`.

2. `MARCADORES-blog-api.txt` registró a las 16:41:32 la edición de `blog-ai/app/esquemas.py`, mientras que `MARCADORES-blog-ai.txt` no existía; esto evidencia que el hook del repositorio de inicio se ejecutó sobre un archivo del repositorio añadido, sin que hubiera evidencia de ejecución del hook propio de este último.
