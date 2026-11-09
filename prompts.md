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
genera un archivo CLAUDE.MD con una sola regla: "este repositorio es el dueño del contenido y todo archivo nuevo debe empezar con un comentario que lo indique"
```

**Qué salió:**  funcionó a la primera

## Prompt 2

**Modelo:** Sonnet 5.5
**Herramienta:** Claude Code

```
ahora generame  un hook que se ejecute al escribir o editar un archivo, mediante PostToolUse para las herramientas Write y Edit. Debe añadir una línea a MARCADORES-<nombre-del-repo>.txt, en la raíz de su propio repositorio, con la fecha, la herramienta utilizada y la ruta del archivo modificado. Siempre usa rutas absolutas: el hook tendrá que registrar cambios en archivos situados fuera de su repositorio.
```

**Qué salió:**  funcionó a la primera

## Prompt 3

**Modelo:** Sonnet 5.5
**Herramienta:** Claude Code

```
ahora agregame un skill sencilla llamada marcador-<nombre-del-repo>, cuya descripción indique a qué repositorio pertenece
```

**Qué salió:** (opcional, una línea) funcionó a la primera 

## Prompt 4

**Modelo:** Sonnet 5.5
**Herramienta:** Claude Code

```
genera un archivo CLAUDE.md en la raiz del proyecto con una sola regla: " los nombres de los campos del contrato público deben escribirse en español, nunca en inglés."
```

**Qué salió:** (opcional, una línea) funcionó a la primera 

## Prompt 5

**Modelo:** Sonnet 5.5
**Herramienta:** Claude Code

```
Añade a la clase ResultadoBusqueda, en ../blog-ai/app/esquemas.py, un campo que indique cuántos fragmentos del artículo han coincidido con la búsqueda. Solo debes modificar ese archivo y utilizar la herramienta de edición de archivos, nunca un script.
```

**Qué salió:** (opcional, una línea) funcionó a la primera 