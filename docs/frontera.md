 
## Qué dijo el agente en el paso 4

### Archivos CLAUDE.md cargados al iniciar la sesión

Al empezar se cargaron dos:

- /home/alberto/IA4Devs/workspace/blog/CLAUDE.md, en la carpeta que contiene los repositorios. Su regla:
▎ Este archivo no vive dentro de ningún repositorio: está en la carpeta que los contiene.
▎ Por eso, toda respuesta que des aquí termina con esta línea, sola y literal:
▎ REGLA-PADRE aplicada: gobierno desde fuera de todos los repositorios.
- /home/alberto/IA4Devs/workspace/blog/blog-api/CLAUDE.md, el del repositorio donde se abrió la sesión. Su regla:
▎ este repositorio es el dueño del contenido y todo archivo nuevo debe empezar con un comentario que lo indique.

blog-ai/CLAUDE.md no se cargó al empezar, aunque blog-ai es un directorio de trabajo adicional. Lo leí yo durante el prompt anterior, antes de tocar esquemas.py. Su regla:

▎ los nombres de los campos del contrato público deben escribirse en español, nunca en inglés.

### Skills disponibles

De los proyectos:
- marcador-blog-api: muestra las últimas líneas de MARCADORES-blog-api.txt.
- marcador-blog-ai: muestra las últimas líneas de MARCADORES-blog-ai.txt. Está disponible aunque la sesión se abrió en blog-api.

Incluidas en Claude Code: dataviz, artifact-design, artifact-diagramming, artifact-capabilities, update-config, keybindings-help, code-review, simplify, fewer-permission-prompts, loop, schedule, claude-api, run, plugin-authoring, init, security-review.

Del paquete anthropic-skills: built-in-browser, chrome-browser, computer-use, deep-research, docs, docx, google-workspace, import-memory, morning, pdf, pptx, skill-creator, xlsx.

### Nombre del campo y por qué

El campo se llama fragmentos_coincidentes (int, valor por defecto 1, mínimo 1):

- En español: ResultadoBusqueda forma parte del contrato público con blog-api, y la regla de blog-ai/CLAUDE.md obliga a escribir esos nombres en español.
- Encaja con los nombres que ya existen: el archivo usa fragmento, fragmentos y fragmentos_indexados. Siguiendo ese patrón, fragmentos_coincidentes dice exactamente qué cuenta: cuántos fragmentos del artículo coincidieron con la consulta.
- Valor por defecto 1 y mínimo 1: si un artículo aparece en los resultados, al menos uno de sus fragmentos ha coincidido. El valor por defecto también evita romper el código que ya crea ResultadoBusqueda.

He registrado este prompt como Prompt 9 en prompts.md.

REGLA-PADRE aplicada: gobierno desde fuera de todos los repositorios.

## Qué encontraste en cada archivo de marcadores

Cada archivo de MARCADORES se edita solamente por acción del hook correspondiente a su repo, aunque puede registrar cambios de ficheros que pertenecen al repo contrario también porque su instrucción no lo limitó, solo pidió agregar una entrada por cada fichero modificado.

en MARCADORES-blog-api:
 
 - están las creaciones de las dos skills porque se hicieron desde la sesión iniciada en blog-api; son dos WRITEs que disparan el hook de blog-api, por lo que se escriben en MARCADORES-blog-api. La norma de que el fichero debe comenzar por un comentario (de blog-api/CLAUDE.md) solo se cumple en la skill de blog-api; NO SE CUMPLE en la skill de blog-ai.
 - está el Edit de esquemas.py por la misma razón, se hizo desde la sesión iniciada en blog-api. Al tocarse un fichero de blog-ai, se cargó antes su correspondiente CLAUDE.md, lo que permitió cumplirse la regla que habla del idioma del campo. También se cumplió la norma del CLAUDE.md de blog/. No sabemos si se habría cumplido la norma del CLAUDE.md de blog-api porque esta habla solamente de ficheros nuevos, y esto era una edición.
 
en MARCADORES-blog-ai:

Este fichero no existe. Nunca se ha llegado a crear, lo que indica que el hook de blog-ai nunca ha llegado a actuar, ni siquiera cuando se agregó el directorio al contexto ni cuando se tocó un fichero de este directorio.


CLAUDE.md de directorios superiores aplican siempre.

CLAUDE.md de segundo directorio carga y aplica al tocar ficheros del segundo directorio.

CLAUDE.md del directorio activo carga siempre, pero aplicó solo al cambio hecho en el fichero del directorio activo (la SKILL).

El hook del directorio activo aplicó siempre, incluso sobre ficheros del segundo directorio. El del segundo directorio no aplicó nunca.
