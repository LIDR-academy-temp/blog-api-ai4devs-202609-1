<!-- blog-api es el dueño del contenido del blog. -->

# Frontera

1. Qué dijo el agente en el paso 4:

   **1. Archivos CLAUDE.md cargados al iniciar la sesión**

   Al arrancar se cargaron dos:

   - **`blog/CLAUDE.md`**, en la carpeta que contiene los repositorios. Su regla, REGLA-PADRE,
     dice: *"toda respuesta que des aquí termina con esta línea, sola y literal: REGLA-PADRE
     aplicada: gobierno desde fuera de todos los repositorios."*
   - **`blog/blog-api/CLAUDE.md`**, en el directorio de trabajo principal. Su regla dice: *"Todo
     archivo nuevo que crees aquí debe empezar con un comentario que lo indique"*, es decir, que
     blog-api es el dueño del contenido del blog. Si el formato no admite comentarios, como
     JSON, hay que avisar.

   El archivo **`blog/blog-ai/CLAUDE.md` no se cargó al iniciar.** Lo leí yo durante la tarea,
   con `cat`, antes de editar. Su regla dice: *"Los nombres de los campos del contrato público
   […] deben escribirse en español, nunca en inglés."*

   Al iniciar también se cargó la memoria `MEMORY.md`, que no es un CLAUDE.md. Contiene una
   entrada sobre registrar los prompts en `prompts.md`.

   **2. Skills disponibles**

   - **Artefactos y documentos:** artifact-design, artifact-diagramming, artifact-capabilities,
     dataviz, anthropic-skills:docs, anthropic-skills:docx, anthropic-skills:pdf,
     anthropic-skills:pptx, anthropic-skills:xlsx, anthropic-skills:google-workspace
   - **Código y revisión:** code-review, simplify, security-review, init, run, claude-api
   - **Configuración de Claude Code:** update-config, keybindings-help,
     fewer-permission-prompts, plugin-authoring
   - **Automatización y tareas programadas:** loop, schedule
   - **Navegador y escritorio:** anthropic-skills:built-in-browser,
     anthropic-skills:chrome-browser, anthropic-skills:computer-use
   - **Otros:** anthropic-skills:deep-research, anthropic-skills:import-memory,
     anthropic-skills:morning, anthropic-skills:skill-creator

   **3. Nombre del campo y motivo**

   Lo llamé **`fragmentos_coincidentes`**, por estas razones:

   - **Regla de blog-ai:** el campo forma parte del contrato público que se publica en
     `openapi.json`, y esa regla exige nombres en español.
   - **Vocabulario del código:** el servicio ya habla de "fragmentos". Están la tabla
     `fragmentos`, el campo `fragmento` y `fragmentos_indexados`.
   - **Significado:** "coincidentes" recoge lo que pediste, los fragmentos del artículo que han
     coincidido con la búsqueda. Así no se confunde con el total de fragmentos indexados del
     artículo.

   REGLA-PADRE aplicada: gobierno desde fuera de todos los repositorios.

2. No encontré archivos de marcadores al preguntarle al a IA por qué me respondió los siguiente:

   Ninguno de los dos archivos existe. Busqué desde `blog/` en todo el árbol, worktrees
   incluidos, y no hay ningún `MARCADORES-*`:

   - `blog-api/MARCADORES-blog-api.txt`: no existe.
   - `blog-ai/MARCADORES-blog-ai.txt`: no existe.

   Lo más probable es que ningún hook se haya ejecutado en esta sesión, aunque edité archivos
   con Write y Edit en los dos repos:

   1. **En blog-api no hay hook en esta rama.** En la rama actual, `frontera-LF`,
      `blog-api/.claude/` solo contiene `worktrees/`. El hook se hizo commit en la rama
      `worktree-hook-marcadores` y solo existe en el worktree
      `.claude/worktrees/hook-marcadores`. Esa rama no se ha fusionado aquí.
   2. **En blog-ai el hook existe, pero esta sesión no lo carga.** Ahí sí están
      `blog-ai/.claude/settings.json` y `hooks/registrar-marcador.sh`. Sin embargo, la sesión
      se abrió en blog-api y blog-ai es solo un directorio de trabajo adicional. Creo que
      Claude Code solo lee el `.claude/settings.json` del proyecto donde se abre la sesión.
      Además, el comando usa `$CLAUDE_PROJECT_DIR`, que aquí apunta a blog-api, y en blog-api
      no existe ese script.

   Para generar los archivos, tendrías que:

   - fusionar `worktree-hook-marcadores` en blog-api, o abrir una sesión en ese worktree;
   - abrir una sesión con blog-ai como directorio principal.