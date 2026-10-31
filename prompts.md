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

**Modelo:** Opus 5.5
**Herramienta:** Claude Code

```
Añade al hardness la siguiente regla: Toda ruta HTTP nueva o modificada debe tener al menos una prueba automatizada que comprueba su código de estado y la estructura de su respuesta JSON.
```

**Qué salió:** Lancé el comando sobre blog-ai en lugar de sobre blog-ai donde no había harness; se creó `blog-ai/CLAUDE.md` con la regla. Reverté el cambio porque no lo lancé correctamente.

## Prompt 2

**Modelo:** Opus 5.5
**Herramienta:** Claude Code

```
Añade la siguiente regla a tu hardness: Toda ruta HTTP nueva o modificada debe tener al menos una prueba automatizada que compruebe su código de estado y la estructura de su respuesta JSON.
```

**Qué salió:** blog-api no tenía harness, así que se creó `blog-api/CLAUDE.md` con la regla. Se añadió dónde viven las rutas (`start/routes.ts`) y las pruebas (`tests/functional/`, Japa), y que hay que comprobar el estado y también la forma del JSON (claves y tipos).

## Prompt 3

**Modelo:** Opus 5.5
**Herramienta:** Claude Code

```
Dame un listado de 10 rutas HTTP incluidas en el proyecto que no tenga pruebas automatizadas.
```

**Qué salió:** El proyecto tiene 14 rutas en `start/routes.ts` y solo 6 no tienen ninguna prueba: `GET /`, `GET /salud`, `GET /contrato`, `POST /buscar`, `POST /preguntar` y `POST /indexar`. No llegaban a 10, así que se listaron esas 6 y se avisó.

## Prompt 4

**Modelo:** Opus 5.5
**Herramienta:** Claude Code

```
.
```

**Qué salió:** El prompt solo tenía un punto, sin ninguna petición. No se hizo nada, salvo registrarlo aquí y preguntar qué se quería.

## Prompt 5

**Modelo:** Opus 5.5
**Herramienta:** Claude Code

```
Crea un CLAUDE.md en la raíz con una sola regla propia del repositorio. En blog-api: este repositorio es el dueño del contenido y todo archivo nuevo debe empezar con un comentario que lo indique. En blog-ai: los nombres de los campos del contrato público deben escribirse en español, nunca en inglés.
```

**Qué salió:** Se creó `blog-api/CLAUDE.md` con la regla del comentario de dueño del contenido, con un ejemplo en TypeScript y un aviso para los formatos que no admiten comentarios, como JSON. También se creó `blog-ai/CLAUDE.md` con la regla de los campos en español, que apunta a `contrato/openapi.json` y `app/esquemas.py`. En ninguno de los dos repos existía ya un `CLAUDE.md`.

## Prompt 6

**Modelo:** Opus 5.5
**Herramienta:** Claude Code

```
Crea un hook en blog-api y otro en blog-ai que se ejecute al escribir o editar un archivo, mediante PostToolUse para las herramientas Write y Edit. Debe añadir una línea a MARCADORES-<nombre-del-repo>.txt, en la raíz de su propio repositorio, con la fecha, la herramienta utilizada y la ruta del archivo modificado. Usa rutas absolutas: el hook tendrá que registrar cambios en archivos situados fuera de su repositorio.
```

**Qué salió:** En cada repo se creó `.claude/settings.json`, con un hook `PostToolUse` (matcher `Write|Edit`), y el script `.claude/hooks/registrar-marcador.sh`. El script saca la raíz absoluta de su repo a partir de su propia ubicación y lee el JSON del hook con `python3`, porque no hay `jq`. Después añade `fecha<TAB>herramienta<TAB>ruta absoluta` a `MARCADORES-blog-api.txt` o a `MARCADORES-blog-ai.txt`. Se probó con archivos de fuera del repo y con rutas relativas. En blog-api se hizo commit en la rama `worktree-hook-marcadores` (el push falló por falta de acceso). En blog-ai los archivos quedaron en el checkout, sin commit.

## Prompt 7

**Modelo:** Opus 5.5
**Herramienta:** Claude Code

```
Escribe una skill sencilla llamada marcador-<nombre-del-repo>, cuya descripción indique a qué repositorio pertenece.
```

**Qué salió:** Se creó `.claude/skills/marcador-blog-api/SKILL.md`. Su descripción dice que pertenece a blog-api y, al invocarla, responde `Marcador: skill de blog-api cargada.` Como el frontmatter YAML tiene que ir primero, el comentario de dueño del contenido se puso como comentario YAML dentro del frontmatter, y también como comentario HTML en el cuerpo. Se hizo commit en la rama `worktree-skill-marcador` (el push falló por falta de acceso).

## Prompt 8

**Modelo:** Opus 5.5
**Herramienta:** Claude Code

```
Añade a la clase ResultadoBusqueda, en ../blog-ai/app/esquemas.py, un campo que indique cuántos fragmentos del artículo han coincidido con la búsqueda. Debes modificar solo ese archivo y utilizar la herramienta de edición de archivos, nunca un script.
```

**Qué salió:** Se añadió `fragmentos_coincidentes: int = Field(default=1, ge=1)` a `ResultadoBusqueda`, con el nombre en español como pide `blog-ai/CLAUDE.md`. Se usó la herramienta Edit y no se tocó ningún otro archivo, así que este prompt no se registró aquí en ese momento. Quedó avisado que `buscar()` en `indice.py` no calcula el campo (siempre vale 1) y que `contrato/openapi.json` no está regenerado.

## Prompt 9

**Modelo:** Opus 5.5
**Herramienta:** Claude Code

```
Responde por separado: Qué archivos CLAUDE.md se cargaron al iniciar la sesión, citando la regla de cada uno.

Qué skills tiene disponibles.

Qué nombre ha dado al campo y por qué.
```

**Qué salió:** Al iniciar se cargaron `blog/CLAUDE.md` (REGLA-PADRE) y `blog-api/CLAUDE.md` (comentario de dueño del contenido). `blog-ai/CLAUDE.md` no se cargó al iniciar; se leyó a mano durante la tarea. Se listaron las skills por grupos y se justificó el nombre `fragmentos_coincidentes`.

## Prompt 10

**Modelo:** Opus 5.5
**Herramienta:** Claude Code

```
Crea el fichero docs/frontera.md
```

**Qué salió:** Se creó `blog-api/docs/frontera.md`, con el comentario HTML de dueño del contenido y el título `# Frontera`. El prompt no decía qué contenido debía llevar, así que el cuerpo quedó vacío.

## Prompt 11

**Modelo:** Opus 5.5
**Herramienta:** Claude Code

```
Desde blog/ lee los dos archivos de marcadores generados y muestrame el contenido
```

**Qué salió:** Ninguno de los dos archivos existe: no está ni `MARCADORES-blog-api.txt` ni `MARCADORES-blog-ai.txt`, ni en la raíz de su repo ni en ningún otro lugar bajo `blog/`. El hook de blog-api solo está en el worktree `hook-marcadores`, no en la rama `frontera-LF`. El de blog-ai existe, pero la sesión se abrió en blog-api, así que no se carga su `settings.json`.

## Prompt 12

**Modelo:** Opus 5.5
**Herramienta:** Claude Code

```
Actualiza el fichero frontera.md punto 1. con el prompt que me devolviste al predirte respondieras por separado qué archivos clause.md se cargaron al inciar la sesión, citando la regla de cada uno. Qué skills tenías disponibles, qué nombre ha dado a cada campo y por qué
```

**Qué salió:** Se copió literalmente, debajo del punto 1 de `docs/frontera.md`, la respuesta que dio el agente al prompt 9 (CLAUDE.md cargados, skills y nombre del campo). Se quitó la línea de terminal que se había pegado por error al final del archivo.

## Prompt 13

**Modelo:** Opus 5.5
**Herramienta:** Claude Code

```
Completa el punto 2. del fichero frontera.md con el motivo por el cuál no se encontraron los ficheros de marcadores
```

**Qué salió:** Se completó el punto 2 de `docs/frontera.md` con la explicación que dio el agente en el prompt 11. En blog-api, el hook solo está en el worktree `hook-marcadores`, sin fusionar en `frontera-LF`. En blog-ai, el hook existe, pero la sesión se abrió en blog-api y no carga su `settings.json`, y `$CLAUDE_PROJECT_DIR` apunta a blog-api. También se incluyó cómo conseguir que se generen los archivos.
