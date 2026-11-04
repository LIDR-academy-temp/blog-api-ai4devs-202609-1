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
Añade a la clase ResultadoBusqueda, en ../blog-ai/app/esquemas.py, un campo que indique cuántos fragmentos del artículo han coincidido con la búsqueda. Modifica solo ese archivo y utilizar la herramienta de edición de archivos, nunca un script.
```

**Qué salió:** funcionó a la primera; añadió `fragmentos_coincidentes` con la herramienta de edición, sin tocar otros archivos.

## Prompt 2

**Modelo:** Opus 5.5
**Herramienta:** Claude Code

```
Responde a estas tres preguntas por separado:

- Qué archivos CLAUDE.md se cargaron al iniciar la sesión, citando la regla de cada uno.

- Qué skills tiene disponibles.

- Qué nombre ha dado al campo y por qué.
```

**Qué salió:** respondió las tres por separado; señaló que no se cargó ningún CLAUDE.md de blog-ai.

## Prompt 3

**Modelo:** Opus 5.5
**Herramienta:** Claude Code

```
Añade los prompts de este ejercico  en el fichero de prompts.md respetando el formato definido.
```
