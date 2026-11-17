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
Monta la misma estructura mínima de gobierno en dos repositorios hermanos: en este (blog-api) y en ../blog-ai. En cada uno de los dos, tres piezas. Primero, un CLAUDE.md en la raíz con UNA regla propia de ese repositorio: la de blog-api es que este repositorio es el dueño del contenido y todo archivo nuevo abre con un comentario que lo diga; la de blog-ai es que los nombres de campo de su contrato público se escriben en español, nunca en inglés. Segundo, un hook PostToolUse que se dispare con Write y con Edit y añada una línea a un archivo MARCADORES-<nombre-del-repo>.txt en la raíz de ese mismo repositorio, con la fecha, la herramienta usada y la ruta del archivo escrito. Que el hook use rutas absolutas, porque va a dispararse sobre archivos que no están en su propio árbol. Tercero, una skill trivial llamada marcador-<nombre-del-repo> cuya descripción diga de qué repositorio es. No toques ningún otro archivo de ninguno de los dos repositorios.
```

**Qué salió:** OK aparentemente. Creo 6 archivos, 3 en cada repositorio.

---

## Prompt 2

**Modelo:** Opus 5.5
**Herramienta:** Claude Code

```
Añade a la clase ResultadoBusqueda de ../blog-ai/app/esquemas.py un campo nuevo que indique cuántos fragmentos del post han coincidido con la búsqueda. Edita solo ese archivo, y edítalo con la herramienta de edición de archivos, nunca con un script de shell. Cuando termines, dime tres cosas por separado: primero, qué archivos CLAUDE.md se te han cargado automáticamente al arrancar, citando de cada uno la regla que contiene; segundo, qué skills tienes disponibles, listando sus nombres; y tercero, qué nombre le has puesto al campo y por qué ese y no otro.
```

**Qué salió:** Ok, creo el archivo `MARCADORES-blog-api.txt`, pero no el del proyecto `blog-ai`.  

---

## Prompt 3

**Modelo:** Opus 5.5
**Herramienta:** Claude Code

```
!(cd .. && echo "--- marcador de blog-api (el repo desde el que arrancamos) ---"; cat blog-api/MARCADORES-blog-api.txt 2>/dev/null || echo "(no existe)"; echo "--- marcador de blog-ai (el repo que anadimos) ---"; cat blog-ai/MARCADORES-blog-ai.txt 2>/dev/null || echo "(NO EXISTE)")
```

**Qué salió:** OK.