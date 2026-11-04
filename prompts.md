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

**Modelo:** Claude 5.5 Sonnet
**Herramienta:** GitHub Copilot (Eclipse - Chat)

```
Crea los archivos de configuración requeridos en blog-api y en ../blog-ai sin modificar nada más:

1. Un archivo .github/copilot-instructions.md en la raíz de blog-api con la regla: "Este repositorio es el dueño del contenido y todo archivo nuevo debe empezar con un comentario que lo indique."
2. Un archivo .github/copilot-instructions.md en la raíz de ../blog-ai con la regla: "Los nombres de los campos del contrato público deben escribirse en español, nunca en inglés."
3. Un hook PostToolUse para las herramientas Write y Edit en cada repositorio que añada la fecha, la herramienta usada y la ruta absoluta del archivo modificado a MARCADORES-blog-api.txt y MARCADORES-blog-ai.txt respectivamente.
4. Una skill sencilla marcador-blog-api y marcador-blog-ai indicando a qué repositorio pertenece cada una.
```

**Qué salió:** Funcionó; creó las reglas de instrucciones (`copilot-instructions.md`), las estructuras de hooks bajo `.claude/` y las definiciones de skills en ambos repositorios.

---

## Prompt 2

**Modelo:** Claude 5.5 Sonnet
**Herramienta:** GitHub Copilot (Eclipse - Chat)

```
Añade a la clase ResultadoBusqueda en ../blog-ai/app/esquemas.py un campo que indique cuántos fragmentos del artículo han coincidido con la búsqueda. Modifica solo ese archivo y utiliza la herramienta de edición de archivos, nunca un script.

Al terminar, responde por separado:
1. Qué archivos de instrucciones (copilot-instructions.md) se cargaron al iniciar la sesión, citando la regla de cada uno.
2. Qué skills tienes disponibles.
3. Qué nombre le diste al campo y por qué.
```

**Qué salió:** Funcionó a la primera; agregó el campo `fragmentos_coincidentes` en español al esquema de `blog-ai` y respondió las 3 preguntas citando las reglas cargadas, las skills disponibles y la justificación del nombre.
