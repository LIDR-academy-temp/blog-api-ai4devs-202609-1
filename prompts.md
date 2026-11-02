## Prompt 1

**Modelo:** Sonnet 5.5
**Herramienta:** Claude Code

```
añada a la clase ResultadoBusqueda, en ../blog-ai/app/esquemas.py, un campo que indique cuántos fragmentos del artículo han coincidido con la búsqueda. Indica que debe modificar solo ese archivo y utilizar la herramienta de edición de archivos, nunca un script.
```

**Qué salió:** funcionó a la primera: añadió `fragmentos_coincidentes` con la herramienta de edición y sin tocar otros archivos.

## Prompt 2

**Modelo:** Sonnet 5.5
**Herramienta:** Claude Code

```
responda por separado:

Qué archivos CLAUDE.md se cargaron al iniciar la sesión, citando la regla de cada uno.

Qué skills tiene disponibles.

Qué nombre ha dado al campo y por qué.
```

**Qué salió:** funcionó a la primera: tres respuestas separadas.

## Prompt 3

**Modelo:** Sonnet 5.5
**Herramienta:** Claude Code

```
deshaz el cambio del campo ejecutando git checkout -- app/esquemas.py dentro de blog-ai y borra el CLAUDE.md de blog/ para que sus instrucciones no sigan aplicándose a los proyectos de esa carpeta.
```

**Qué salió:** funcionó a la primera: revisó el diff antes del checkout y borró el `CLAUDE.md` de `blog/`.

## Prompt 4

**Modelo:** Sonnet 5.5
**Herramienta:** Claude Code

```
prompts.md es una plantilla. Léela y rellénala de acuerdo a las instrucciones, completándola con todos los prompts de hoy relativos a blog-api y blog-ai
```

**Qué salió:** este mismo archivo. Solo he podido recoger los prompts de esta sesión; si hubo otros hoy en otras sesiones, hay que añadirlos a mano.
