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

**Modelo:** Opus 5.5
**Herramienta:** Claude Code

```
Dame un resumen de lo que hace el proyecto
```

**Qué salió:** resumen del README, las rutas y el contrato con blog-ai, a la primera.

## Prompt 2

**Modelo:** Opus 5.5
**Herramienta:** Claude Code

```
Quiero que me crees dentro de los repositorios de blog-api y blog-ai los siguientes ficheros:
Un CLAUDE.md en la raíz con una sola regla propia del repositorio. En blog-api: este repositorio es el dueño del contenido y todo archivo nuevo debe empezar con un comentario que lo indique. En blog-ai: los nombres de los campos del contrato público deben escribirse en español, nunca en inglés. Las reglas son distintas para poder reconocer después cuál se aplicó.

Un hook que se ejecute al escribir o editar un archivo, mediante PostToolUse para las herramientas Write y Edit. Debe añadir una línea a MARCADORES-<nombre-del-repo>.txt, en la raíz de su propio repositorio, con la fecha, la herramienta utilizada y la ruta del archivo modificado. Pide que use rutas absolutas: el hook tendrá que registrar cambios en archivos situados fuera de su repositorio.

Una skill sencilla llamada marcador-<nombre-del-repo>, cuya descripción indique a qué repositorio pertenece.

Una vez creados no cambies nada más
```

**Qué salió:** creó CLAUDE.md, `.claude/settings.json`, `.claude/hooks/marcador.sh` y la skill en los dos repos; avisó de que el hook se carga al arrancar la sesión y de que existe un CLAUDE.md en la carpeta padre que no se cargó.

## Prompt 3

**Modelo:** Opus 5.5
**Herramienta:** Claude Code

```
guarda en el fichero prompts.md los prompts ejecutados en esta sesion
```

## Prompt 4

**Modelo:** Opus 5.5
**Herramienta:** Claude Code

```
Añade a la clase ResultadoBusqueda, en ../blog-ai/app/esquemas.py, un campo que indique cuántos fragmentos del artículo han coincidido con la búsqueda. Debes modificar solo ese archivo y utilizar la herramienta de edición de archivos, nunca un script
```

**Qué salió:** añadió `fragmentos_coincidentes: int = Field(default=1, ge=1)` con la herramienta Edit, tocando solo `esquemas.py`; avisó de que `contrato/openapi.json` queda desactualizado. Terminó con la línea de la REGLA-PADRE.

## Prompt 5

**Modelo:** Opus 5.5
**Herramienta:** Claude Code

```
Ahora quiero que me contestes a estos tres bloques por separado, Utiliza tablas para cada uno de ellos: 

Qué archivos CLAUDE.md se cargaron al iniciar la sesión, citando la regla de cada uno.

Qué skills tiene disponibles.

Qué nombre ha dado al campo y por qué.
```

**Qué salió:** tres tablas. Se cargaron dos CLAUDE.md (el de la carpeta padre con la REGLA-PADRE y el de blog-api); el de blog-ai no se cargó. Listó las skills, con `marcador-blog-api` y `marcador-blog-ai` entre ellas, y justificó el nombre `fragmentos_coincidentes`.

## Prompt 6

**Modelo:** Opus 5.5
**Herramienta:** Claude Code

```
guarda en el fichero prompts.md los prompts ejecutados en esta sesion
```

**Qué salió:** añadió los prompts 4 a 6 a este archivo.
