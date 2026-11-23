# Prompts

Aquí van **todos los prompts que lanzaste** para hacer el ejercicio, en el orden en que los
lanzaste, con el modelo y la herramienta de cada uno.

Esto no es papeleo. Lo que se revisa es **cómo pediste las cosas**, no solo lo que salió: un
resultado flojo con un prompt bueno y un resultado flojo con un prompt vago necesitan feedback
distinto, y sin este archivo no se distinguen.

## Cómo rellenarlo

- Un apartado `## Prompt N` por cada prompt.
- **Pega el prompt tal cual lo lanzaste**, dentro del bloque de código, aunque ocupe diez líneas
  y aunque tenga faltas. No lo reescribas para que quede bien: el que arreglaste mentalmente
  después no es el que lanzaste.
- Incluye también los que **no funcionaron**. Suelen ser los más útiles de leer.
- `Modelo` y `Herramienta` en todos. Si cambiaste de una a otra a mitad, se nota aquí.

Borra el ejemplo de abajo cuando escribas el primero.

---

## Prompt 1

**Modelo:** Sonnet 5.5
**Herramienta:** Claude Code

```
Vamos a montar un harness incial en el repositorio de este proyecto y en el de ../blog-ai. Primero agregar un CLAUDE.md en la raiz de cada uno y con reglas propias para cada proyecto. En blog-api: este repositorio es el dueño del contenido y todo archivo nuevo debe empezar con un comentario que lo indique. En blog-ai: los nombres de los campos del contrato público deben escribirse en español, nunca en inglés. Las reglas son distintas para poder reconocer después cuál se aplicó. No hagas nada mas y espera mi siguiente instrucción.
```

**Qué salió:** creó los dos CLAUDE.md con una regla distinta cada uno.

## Prompt 2

**Modelo:** Sonnet 5.5
**Herramienta:** Claude Code

```
Ahora agrega para ambos repositorios un hook que se ejecute al escribir o editar un archivo, mediante PostToolUse para las herramientas Write y Edit. Se debe añadir una línea a MARCADORES-<nombre-del-repo>.txt, en la raíz de su propio repositorio, con la fecha, la herramienta utilizada y la ruta del archivo modificado. Se tienen que usar rutas absolutas ya que el hook tendrá que registrar cambios en archivos situados fuera de su repositorio. No hagas nada más y espera mi siguiente instrucción.
```

**Qué salió:** creó `.claude/settings.json` y `.claude/hooks/marcador.sh` en los dos repositorios.

## Prompt 3

**Modelo:** Sonnet 5.5
**Herramienta:** Claude Code

```
Ahora agrega una skill sencilla llamada marcador-<nombre-del-repo>, cuya descripción indique a qué repositorio pertenece. No hagas nada más y espera mi siguiente instrucción.
```

**Qué salió:** creó `.claude/skills/marcador-blog-api/SKILL.md` y `.claude/skills/marcador-blog-ai/SKILL.md`.

## Prompt 4

**Modelo:** Sonnet 5.5
**Herramienta:** Claude Code

```
ñade a la clase ResultadoBusqueda, en ../blog-ai/app/esquemas.py, un campo que indique cuántos fragmentos del artículo han coincidido con la búsqueda. Únicamente debe modificar ese archivo y ningún otro y debes utilizar la herramienta de edición de archivos y de ninguna manera un script.
Al terminar, dame una respuesta por separado para los siguientes puntos:
- Qué archivos CLAUDE.md se cargaron al iniciar la sesión, citando la regla de cada uno.
- Qué skills tienes disponibles.
- Qué nombre has dado al campo y por qué.
```

**Qué salió:** Añadí el campo fragmentos_coincidentes a ResultadoBusqueda en ../blog-ai/app/esquemas.py.

1. Archivos CLAUDE.md cargados al iniciar la sesión
- /home/germanny21/projects/lidr/blog/CLAUDE.md (REGLA-PADRE): "toda respuesta que des aquí termina con esta línea, sola y literal" (la línea final de este mensaje).
- /home/germanny21/projects/lidr/blog/blog-api/CLAUDE.md: "Todo archivo nuevo debe empezar con un comentario que indique que este repositorio es el dueño del contenido." Aquí no aplica, porque edité un archivo existente y no creé ninguno.
- blog-ai/CLAUDE.md no se cargó al iniciar, porque blog-ai es un directorio adicional. Lo leí después, al preparar la edición. Su regla es: "Los nombres de los campos del contrato público se escriben en español, nunca en inglés."

2. Skills disponibles
- Del proyecto: marcador-blog-api y marcador-blog-ai.
- PDF: pdf-viewer:annotate, pdf-viewer:fill-form, pdf-viewer:open, pdf-viewer:sign, pdf-viewer:view-pdf y anthropic-skills:pdf.
- Desktop Commander: ai-tools-setup, computer-health-check, desktop-commander-overview, knowledge-base, obsidian-vault y terminal.
- Ingeniería: architecture, code-review, debug, deploy-checklist, documentation, incident-response, standup, system-design, tech-debt y testing-strategy.
- Revisión y entrega: code-review, simplify, security-review, ship-local (/ship), steward y claude-approvals.
- Configuración y automatización: update-config, keybindings-help, fewer-permission-prompts, loop, schedule, init, run, plugin-authoring y claude-api.
- Artefactos y gráficos: dataviz, artifact-design, artifact-diagramming y artifact-capabilities.
- Otras de anthropic-skills: built-in-browser, chrome-browser, computer-use, deep-research, docs, docx, google-workspace, import-memory, morning, pptx, setup-writing-style, skill-creator y xlsx.

3. Nombre del campo y por qué
- Nombre: fragmentos_coincidentes, de tipo int.
- Idioma: la regla de blog-ai/CLAUDE.md exige español en los campos del contrato público. ResultadoBusqueda forma parte de ese contrato, así que descarté nombres como matched_chunks.
- Coherencia: RespuestaIndexar.fragmentos y fragmento ya usan "fragmento" para lo que el código llama chunk, y el nuevo nombre sigue esa terminología.
- Valor por defecto: Field(default=1, ge=1), porque un resultado solo existe si coincidió al menos un fragmento. Con el valor por defecto, el código que ya construye ResultadoBusqueda no falla. Ese código tampoco informa el número real hasta que se actualice.
- Contrato versionado: contrato/openapi.json queda desactualizado, porque me limité a ese único archivo. Habrá que regenerarlo aparte.

REGLA-PADRE aplicada: gobierno desde fuera de todos los repositorios..
