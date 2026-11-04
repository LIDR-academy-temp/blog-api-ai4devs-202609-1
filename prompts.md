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

---

## Prompt 1

**Modelo:** Sonnet 5.5
**Herramienta:** Claude Code

```
Crea un CLAUDE.md con una sola regla en los repositorios blog-api y blog-ai. blog-api es este repositorio, blog-ai se encuentra en uno de los directorios hermanos a este. Las reglas para cada repo seran: En blog-api: este repositorio es el dueño del contenido y todo archivo nuevo debe empezar con un comentario que lo indique. En blog-ai: los nombres de los campos del contrato público deben escribirse en español, nunca en inglés. Las reglas son distintas para poder reconocer después cuál se aplicó.
```

**Qué salió:** funcionó a la primera: creé `blog-api/CLAUDE.md` y `blog-ai/CLAUDE.md` (localizado como carpeta hermana), cada uno con su única regla; no hice commit.

## Prompt 2

**Modelo:** Sonnet 5.5
**Herramienta:** Claude Code

```
Ahora crea un hook que se ejecute al escribir o editar un archivo, mediante PostToolUse para las herramientas Write y Edit. Debe añadir una línea a MARCADORES-<nombre-del-repo>.txt, en la raíz de su propio repositorio, con la fecha, la herramienta utilizada y la ruta del archivo modificado. Usa rutas absolutas, el hook tendrá que registrar cambios en archivos situados fuera de su repositorio.
```

**Qué salió:** funcionó a la primera: creé `.claude/settings.json` (PostToolUse, matcher `Write|Edit`) y `.claude/hooks/marcador.mjs`, que escribe en `MARCADORES-blog-api.txt`; lo probé a mano con una ruta de `blog-ai` y registró bien, pero no se ha probado dentro de una sesión real.

## Prompt 3

**Modelo:** Sonnet 5.5
**Herramienta:** Claude Code

```
Por ultimo, crea una skill sencilla llamada marcador-<nombre-del-repo>, cuya descripción indique a qué repositorio pertenece
```

**Qué salió:** funcionó a la primera: creé `.claude/skills/marcador-blog-api/SKILL.md`, cuya descripción dice que es de blog-api y que muestra los últimos cambios de `MARCADORES-blog-api.txt`; el comentario de propiedad del repo va tras el frontmatter para no romper la skill, y no la he invocado.

## Prompt 4

**Modelo:** Sonnet 5.5
**Herramienta:** Claude Code

```
Ahora he de cerrar la sesión para cargar todos estos guardarrailes. Necesito que al volver a abrirla continues guardando los prompts
```

**Qué salió:** funcionó a la primera: actualicé mi memoria del proyecto con el estado del registro (último apartado `## Prompt 4`, siguiente `## Prompt 5`) para retomarlo al reabrir la sesión.

## Prompt 5

**Modelo:** Sonnet 5.5
**Herramienta:** Claude Code

```
Añade a la clase ResultadoBusqueda, en ../blog-ai/app/esquemas.py, un campo que indique cuántos fragmentos del artículo han coincidido con la búsqueda. Debes  modificar solo ese archivo y utilizar la herramienta de edición de archivos, nunca un script
```

**Qué salió:** funcionó a la primera: con la herramienta Edit añadí `fragmentos_coincidentes: int = Field(default=1, ge=1)` a `ResultadoBusqueda`, sin tocar otros archivos; el valor por defecto es 1, así que nada lo calcula todavía, y no regeneré `contrato/openapi.json` ni ejecuté tests. No lo registré aquí en su momento; se recuperó después.

## Prompt 6

**Modelo:** Sonnet 5.5
**Herramienta:** Claude Code

```
Qué archivos CLAUDE.md se cargaron al iniciar la sesión? Cita las reglas de cada uno
```

**Qué salió:** funcionó a la primera: listé los dos `CLAUDE.md` cargados (el de `blog/` con la REGLA-PADRE y el de `blog-api/` con la regla de propiedad) y el índice de memoria, citando sus reglas; respondí de memoria del contexto, sin releer los archivos. Tampoco lo registré en su momento.

## Prompt 7

**Modelo:** Sonnet 5.5
**Herramienta:** Claude Code

```
que skills tienes disponibles?
```

**Qué salió:** funcionó a la primera: listé las skills del contexto, agrupadas en la del repositorio (`marcador-blog-api`), las integradas de Claude Code y las de documentos (`anthropic-skills:*`); respondí de la lista cargada, sin invocar ninguna.

## Prompt 8

**Modelo:** Sonnet 5.5
**Herramienta:** Claude Code

```
Que nombre le has dado al campo de ResultadoBusqueda y por qué?
```

**Qué salió:** funcionó a la primera: expliqué que el campo es `fragmentos_coincidentes`, en español y en plural para distinguirlo de `fragmento` y de `fragmentos` de `RespuestaIndexar`; aclaré que la razón fue la coherencia con los nombres que vi en `esquemas.py`, no una regla de `blog-ai/CLAUDE.md`, que no se cargó en la sesión.

## Prompt 9

**Modelo:** Sonnet 5.5
**Herramienta:** Claude Code

```
Parece que nos saltamos un paso. En la sesión anterior te pedi: Crea un  hook que se ejecute al escribir o editar un archivo, mediante PostToolUse para las herramientas Write y Edit. Debe añadir una línea a MARCADORES-<nombre-del-repo>.txt, en la raíz de su propio repositorio, con la fecha, la herramienta utilizada y la ruta del archivo modificado. Usa rutas absolutas: el hook tendrá que registrar cambios en archivos situados fuera de su repositorio. |||| Tambien falta la skill.  Solo parecen haberse creado en blog-api y no en blog-ai. Crealos en blog-ai basandote en blog-api y fuerza a que se generen como deberían haberse generado cuando te pedi que añadieses el nuevo campo
```

**Qué salió:** funcionó, con una salvedad: creé en `blog-ai` `.claude/settings.json`, `.claude/hooks/marcador.mjs` y `.claude/skills/marcador-blog-ai/SKILL.md`, copiados de blog-api con el nombre y el comentario adaptados, y una línea de `MARCADORES-blog-ai.txt` reconstruida a mano con la hora real de la edición de `esquemas.py` (13:22:51Z) tomada del log de blog-api. Probé el hook con una entrada simulada y funcionó; esa línea de prueba la borré del log. El hook de blog-ai solo se activa en sesiones abiertas desde `blog-ai`, y la skill no la he invocado. Además, el hook de blog-api registró aquella edición en `MARCADORES-blog-api.txt` y esa línea sigue allí.

## Prompt 10

**Modelo:** Sonnet 5.5
**Herramienta:** Claude Code

```
En docs/frontera.md preguntame por las respuestas a las 2 siguientes preguntas y dejalas escritas allí en funcion de lo que te responda Qué dijo el agente en el paso 4? Qué encontraste en cada archivo de marcadores y qué indica sobre dónde se ejecuta cada guardarraíl?
```

**Qué salió:** a medias: `docs/frontera.md` no existía (el README pide crear `docs/` en blog-api), así que no he escrito nada todavía; te hice las dos preguntas y espero tus respuestas para redactar el archivo. (Continúa en el Prompt 11.)

## Prompt 11

**Modelo:** Sonnet 5.5
**Herramienta:** Claude Code

```
1. Cuando te pedi añadir el campo. Indica qué archivos CLAUDE.md cargastes, que skills tenias disponibles y que nombre le distes al campo
```

**Qué salió:** a medias: con tu respuesta a la pregunta 1 creé `blog-api/docs/frontera.md` (con el comentario de propiedad inicial) con una sola frase, redactada desde lo que sé de aquel momento (dos `CLAUDE.md` cargados, skill `marcador-blog-api`, campo `fragmentos_coincidentes`); falta la pregunta 2 porque no la has respondido, y no he inventado esa segunda frase.

## Prompt 12

**Modelo:** Sonnet 5.5
**Herramienta:** Claude Code

```
En la pregunta 2: indica que se ejecuta cada skill de su repo y luego se edita /blog-ai/app/esquemas.py
```

**Qué salió:** funcionó con una salvedad: añadí la segunda frase a `docs/frontera.md` describiendo esa prueba y lo que muestran los archivos (edición de `blog-ai` y todas las demás en `MARCADORES-blog-api.txt`; solo mi línea manual en `MARCADORES-blog-ai.txt`), pero interpreté tu frase como el contenido a escribir: no he ejecutado las skills ni he vuelto a editar `esquemas.py`, así que la conclusión sale de los archivos tal como están.
