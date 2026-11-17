# Parte B: las 2 lineas

1. Qué dijo el agente en el paso 4: 
	- Qué archivos CLAUDE.md dijo haber cargado:
		Archivos CLAUDE.md cargados al arrancar
			- C:\Users\maxxi\Documents\Ejercicios\blog\CLAUDE.md: la REGLA-PADRE. Toda respuesta termina con la línea literal «REGLA-PADRE aplicada: gobierno desde fuera de todos los repositorios.»
			- C:\Users\maxxi\Documents\Ejercicios\blog\blog-api\CLAUDE.md: todo archivo nuevo que se cree en blog-api abre con un comentario que diga «Este archivo es contenido de blog-api, dueño del contenido.» Aquí no se aplica, porque no he creado ningún archivo, y menos en blog-api.
		No se cargó ningún CLAUDE.md de blog-ai, aunque es el repositorio que he editado.
	- Qué skills tenía disponibles:
		Skills disponibles
			marcador-blog-api, marcador-blog-ai, dataviz, artifact-design, artifact-diagramming, artifact-capabilities, update-config, keybindings-help, code-review, simplify, fewer-permission-prompts, loop, schedule, claude-api, claude-in-chrome, run, plugin-authoring, init, security-review, anthropic-skills:built-in-browser, anthropic-skills:chrome-browser, anthropic-skills:computer-use, anthropic-skills:deep-research, anthropic-skills:docs, anthropic-skills:docx, anthropic-skills:import-memory, anthropic-skills:morning, anthropic-skills:pdf, anthropic-skills:pptx, anthropic-skills:skill-creator,anthropic-skills:xlsx.
	- Qué nombre dio al campo:
		Por qué fragmentos_coincidentes
			- Sigue cómo se nombra en el archivo: las cantidades se escriben en plural y sin prefijo (indexados, omitidos, fragmentos en RespuestaIndexar), con un adjetivo cuando hace falta precisar (fragmentos_indexados en RespuestaSalud). fragmentos_coincidentes sigue ese mismo patrón.
			- No se confunde con lo que ya existe: fragmentos a secas podría leerse como el total de fragmentos del post. Algo como num_fragmentos o coincidencias rompería el estilo o no diría qué se cuenta. Además, el nombre deja claro que fragmento es solo el mejor de esos fragmentos.
			- No rompe el contrato: el campo es parte del contrato público que consume blog-api. Lleva valor por defecto para que el código que ya crea resultados sin él siga funcionando. Ese valor es 1 con ge=1 porque todo resultado tiene al menos un fragmento coincidente, el que va en fragmento.

2. Qué encontraste en cada archivo de marcadores y qué indica sobre dónde se ejecuta cada guardarraíl.
	- No se creó el archivo del lado del proyecto/repositorio `blog-ai`. Esto quiere decir que al estar sobre el proyecto `blog-api` los guardarraíles de `blog-ai` no se accionaron.
	- Por otro lado, si se creó el archivo `MARCADORES-blog-api.txt`. Pero un punto que llama la atensión es que sobre este se ingresa el hecho de la modificación de un archivo del proyecto de `blog-ai`.
	Justamente esto fue lo reflejado por el agente Claude luego del prompt 3:
		> "- Hooks: Claude Code toma los ajustes del proyecto de la carpeta desde la que arrancó, no de los directorios añadidos. El hook se dispara en cualquier Edit de la sesión, sea cual sea el repositorio del archivo. Por eso blog-api registró una edición que no era suya, y la de blog-ai no la registró nadie.
		> - CLAUDE.md: el de blog-ai tampoco se cargó. Lo he leído ahora y su regla es: «Los nombres de campo del contrato público de este repositorio (contrato/) se escriben en español, nunca en inglés». fragmentos_coincidentes la cumple, pero por casualidad: yo no conocía esa regla.
		> - Skills: las del directorio añadido sí aparecieron. Es la única de las tres cosas que pasó de blog-ai a la sesión.
		> 
		> Para que blog-ai se rija por sus propias reglas y hooks, la sesión tendría que arrancar dentro de blog-ai."
	