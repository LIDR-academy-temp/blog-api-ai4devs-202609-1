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
Realiza un resumen breve del proyecto. Verifica que puedas ejecutar comandos. No modifiques nada.
```

**Qué salió:** Funcionó. Me genero el resumen y me indico que si puede ejecutar comandos BASH.
Nota: Si envío el mismo comando en el repo de blog-ai. De igual forma, se retorno el resumen y se indica que si existe permisos para ejecución de comandos.

## Prompt 2

**Modelo:** Sonnet 5.5
**Herramienta:** Claude Code

```
Identifica el archivo de instrucción para el agente, si existe. Identifica las comprobaciones automaticas que se ejecutan al editar archivos o integrar cambios, si los hay. Identifica los atajos del equipo, si los hay. Lista esta información para que la pueda ubicar.
```

**Qué salió:** Funcionó. Listo los hallazgos. No existe archivo de instrucciones ni hooks o skills. Solo existen archivos que facilitan la configuración y ejecución (make).
Nota: Mismo caso con el repo de blog-ai.

## Prompt 3

**Modelo:** Sonnet 5.5
**Herramienta:** Claude Code

```
Crea lo siguiente tanto en el repositorio blog-api como en el repositorio blog-ai (que se encuentra dentro de la carpeta raiz /blog):

1. Un CLAUDE.md en la raíz con una sola regla propia del repositorio. En blog-api: este repositorio es el dueño del contenido y todo archivo nuevo debe empezar con un comentario que lo indique. En blog-ai: los nombres de los campos del contrato público deben escribirse en español, nunca en inglés. Es un archivo CLAUDE.md por repositorio (no lo olvides).

2. Un hook que se ejecute al escribir o editar un archivo, mediante PostToolUse para las herramientas Write y Edit. Es un hook por repositorio (no lo olvides). Adicionalmente, por cada repositorio se deberá crear un archivo con el siguiente nombre MACADORES-<nombre-del-repositorio>.txt en el cual se deberá agregar registros que contendran: fecha, herramienta utilizada y la ruta absoluta. Los registros en el archivo MACADORES-<nombre-del-repositorio>.txt serán por cada archivo escrito o modificado. Si alguno de los hooks toca archivos fuera de su repositorio igual deberá registrarlos.El nombre de los hooks queda a tu consideración.

3. Un skill con el nombre marcador-<nombre-del-repositorio>. Recuerda que es un skill por cada repositorio (no lo olvides). Este skill, deberá tener en su descripción indicando a que repositorio pertenece. La skill segun su repositorio será la utilizada por el hook para realizar el registro en el archivo de texto.

```

**Qué salió:** Generó los archivos solicitados con las especificaciones dadas. Los archivos de texto indicó que no se crean, se crearán hasta que se requieran los registros.


## Prompt 4

**Modelo:** Sonnet 5.5
**Herramienta:** Claude Code

```
Añade a la clase ResultadoBusqueda, en ../blog-ai/app/esquemas.py, un campo que indique cuántos fragmentos del articulo han coincidido con la búsqueda. Solo modifica este archivo y solo utiliza la herramienta de edición de archivos, no uses scripts para este encargo.

```

**Qué salió:** Realizó el encargo correctamente. Realizó el registro de la modificación en el archivo MARCADORES de blog-api, en blog-ai no realizó el registro (El agente indica que no pudo verificar que el hook marcador-blog-ai hubiera hecho el registro, se verifica y se confirma que no se realizó debido a que el archivo no existe). De igual forma, el agente indica que no agrega el comentario del dueño del contenido al archivo debido a que la regla pertence a blog-api (haciendo referencia a que lo se modifico fue en blog-ai) y que el archivo no fue creado sino que ya existía y solo fue modificado.

## Prompt 5

**Modelo:** Sonnet 5.5
**Herramienta:** Claude Code

```
Para el encargo anterior, indica lo siguiente:

1. ¿Que archivos CLAUDE.md se cargaron al iniciar la sesión? Cita la regla de cada uno según los cargados.
2. ¿Que skills tienes disponibles?
3. ¿Que nombre has dado al campo y por qué?
```

**Qué salió:** Indicó que se cargó el CLAUDE.md de la carpeta raiz (/blog) y el CLAUDE.md del repo actual (blog-api). Skills disponibles tiene el que creamos para el repositorio blog-api y algunos adicionales de Claude Code. El nombre fue 'fragmentos_coincidentes' y fue en español por consideración de los atributos del mismo archivo, no por alguna regla.






