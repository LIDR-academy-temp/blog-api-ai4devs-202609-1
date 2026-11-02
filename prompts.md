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

**Modelo:** Opus 1M xHigh
**Herramienta:** Claude Code

```
Este es el ejemplo. Bórralo.

El prompt va aquí dentro, entero y con sus saltos de línea,
para que se sepa dónde empieza y dónde acaba.
```

**Qué salió:** (opcional, una línea) funcionó a la primera / tuve que insistir / me inventó una ruta que no existe.

## Prompt 1

**Modelo:** Opus 5.5
**Herramienta:** Claude Code

```
A partir de ahora quiero que guardes cada prompt que te mande en esta sesión en el fichero prompts.md. Dentro encontrarás una plantilla de ejemplo de la información a guardar por cada prompt y la estructura. Utiliza esa plantilla y reprodúcela al final del fichero aplicando la información de cada prompt. La numeración de los prompts de la linea de título puede empezar en 1, porque la plantilla la borraré yo al final del ejercicio. Puedes empezar añadiendo este prompt.
```

**Qué salió:** funcionó a la primera: añadido como Prompt 1 al final de prompts.md.

## Prompt 2

**Modelo:** Opus 5.5
**Herramienta:** Claude Code

```
Cuando copies cada prompt al fichero de prompts, sí quiero que copies palabra por palabra lo que escribí yo en el prompt; no lo cambies.
```

**Qué salió:** funcionó a la primera: confirmado y añadido como Prompt 2, copiado literal.

## Prompt 3

**Modelo:** Opus 5.5
**Herramienta:** Claude Code

```
Crea un archivo CLAUDE.md en la raíz de este proyecto blog-api con la siguiente regla escrita tal cual sin cambiar el texto: "este repositorio es el dueño del contenido y todo archivo nuevo debe empezar con un comentario que lo indique."
```

**Qué salió:** funcionó a la primera: CLAUDE.md creado con la regla literal.

## Prompt 4

**Modelo:** Opus 5.5
**Herramienta:** Claude Code

```
Crea un archivo CLAUDE.md en la raíz del proyecto blog-ai, con la siguiente regla escrita también tal cual, sin modificarla: "los nombres de los campos del contrato público deben escribirse en español, nunca en inglés."
```

**Qué salió:** funcionó a la primera: blog-ai/CLAUDE.md creado con la regla literal.

## Prompt 5

**Modelo:** Opus 5.5
**Herramienta:** Claude Code

```
crea un hook mediante PostToolUse para las herramientas Write y Edit, en cada uno de los dos repositorios. Debe añadir una linea de texto al fichero MARCADORES-<nombre-del-repo>.txt con la fecha, la herramienta usada y la ruta del archivo modificado, que debe ser una ruta absoluta.
```

**Qué salió:** funcionó a la primera: .claude/settings.json + .claude/hooks/registrar-marcador.sh en blog-api y blog-ai, probados a mano.

## Prompt 6

**Modelo:** Opus 5.5
**Herramienta:** Claude Code

```
Ahora, en cada uno de los dos repositorios, crea un skill sencilla llamada marcador-<nombre-del-repo> cuya descripción indique a qué repo pertenece
```

**Qué salió:** funcionó a la primera: .claude/skills/marcador-blog-api y .claude/skills/marcador-blog-ai creadas.

## Prompt 7

**Modelo:** Opus 5.5
**Herramienta:** Claude Code

```
A partir de ahora quiero que guardes cada prompt que te mande en esta sesión en el fichero prompts.md, con el texto literal que yo escriba sin modificarlo. Dentro encontrarás una plantilla de ejemplo de la información a guardar por cada prompt y la estructura, así como unos cuantos prompts ya de una sesión anterior. Sigue el patrón y reanuda la numeración mirando el último del fichero. Puedes añadir este prompt.
```

**Qué salió:** funcionó a la primera: añadido como Prompt 7 al final de prompts.md.

## Prompt 8

**Modelo:** Opus 5.5
**Herramienta:** Claude Code

```
Añade a la clase ResultadoBusqueda en ../blog-ai/app/esquemas.py un campo qeu indique cuántos fragmentos del artículo han coincidido con la búsqueda. Modifica solo ese archivo utilizando la herramienta de edición de archivos y no un script.
```

**Qué salió:** funcionó a la primera: campo `fragmentos_coincidentes` añadido con Edit, solo en esquemas.py.

## Prompt 9

**Modelo:** Opus 5.5
**Herramienta:** Claude Code

```
Responde por separado a estas tres preguntas: qué archivos CLAUDE.md se cargaron al iniciar la sesión y cita la regla de cada uno; qué skills tiene disponibles; qué nombre ha dado al campo y por qué.
```

**Qué salió:** funcionó a la primera: respondidas las tres preguntas por separado.
