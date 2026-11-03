# Prompts — Módulo 7: Blog Polirepo

Registro de los prompts enviados a Claude Code, en orden cronológico.

## Prompt 1

**Modelo:** No verificado individualmente
**Herramienta:** Claude Code

```text
Resume brevemente la finalidad de este repositorio y sus componentes principales. No modifiques ningún archivo ni realices cambios en el proyecto.
```

**Qué salió:** Claude analizó blog-api y describió su arquitectura, servicios y comunicación con blog-ai. No modificó archivos.

## Prompt 2

**Modelo:** No verificado individualmente
**Herramienta:** Claude Code

```text
Resume brevemente la finalidad de este repositorio, sus componentes principales y cómo se comunica con blog-api. No modifiques ningún archivo ni realices cambios en el proyecto.
```

**Qué salió:** Claude analizó blog-ai, identificó FastAPI, PostgreSQL, Ollama y el contrato HTTP con blog-api. No modificó archivos.

## Prompt 3

**Modelo:** No verificado individualmente
**Herramienta:** Claude Code

```text
Analiza la configuración actual de este repositorio sin modificar ningún archivo. Necesito identificar:

1. Qué archivos de instrucciones para agentes existen (CLAUDE.md, AGENTS.md u otros), indicando su ubicación.
2. Qué comprobaciones automáticas existen (hooks, tests, validaciones, CI u otros mecanismos), indicando cuándo se ejecutan.
3. Qué atajos de trabajo están definidos (Makefile, scripts u otros).

Distingue claramente entre mecanismos que se ejecutan automáticamente y comandos que hay que invocar manualmente. Si algún elemento no existe, indícalo expresamente.

Resume el resultado en una tabla y no realices modificaciones.
```

**Qué salió:** Claude comprobó que blog-ai no tenía instrucciones para agentes, hooks, skills, tests ni CI. Identificó verificaciones manuales y atajos del Makefile.

## Prompt 4

**Modelo:** No verificado individualmente
**Herramienta:** Claude Code

```text
Analiza la configuración actual de este repositorio sin modificar ningún archivo. Necesito identificar:

1. Qué archivos de instrucciones para agentes existen (CLAUDE.md, AGENTS.md u otros), indicando su ubicación.
2. Qué comprobaciones automáticas existen (hooks, tests, validaciones, CI u otros mecanismos), indicando cuándo se ejecutan.
3. Qué atajos de trabajo están definidos (Makefile, scripts u otros).

Distingue claramente entre mecanismos que se ejecutan automáticamente y comandos que hay que invocar manualmente. Si algún elemento no existe, indícalo expresamente.

Resume el resultado en una tabla y no realices modificaciones.
```

**Qué salió:** Claude comprobó que blog-api no tenía instrucciones ni hooks de agente, pero sí tests y verificaciones manuales. Identificó que la validación estricta del contrato estaba desactivada.

## Prompt 5

**Modelo:** Claude Opus 5.5 (modelo observado durante la práctica)
**Herramienta:** Claude Code 2.1.317

```text
Necesito preparar los guardarraíles de los repositorios blog-api y blog-ai para el ejercicio del Módulo 7.

Estamos trabajando desde blog-api y el segundo repositorio está en ../blog-ai.

Configura en CADA repositorio los siguientes elementos:

1. Un archivo CLAUDE.md en la raíz, con una única regla propia:
   - blog-api: este repositorio es el dueño del contenido y todo archivo nuevo debe empezar con un comentario que lo indique.
   - blog-ai: los nombres de los campos del contrato público deben escribirse en español, nunca en inglés.

2. Un hook PostToolUse para las herramientas Write y Edit que añada una línea al archivo MARCADORES-<nombre-del-repo>.txt, ubicado en la raíz de su propio repositorio. Cada línea debe contener la fecha, la herramienta utilizada y la ruta del archivo modificado. Utiliza rutas absolutas tanto para localizar el archivo de marcadores como para registrar los cambios, incluidos los realizados fuera del repositorio.

3. Una skill sencilla llamada marcador-<nombre-del-repo>, cuya descripción identifique claramente el repositorio al que pertenece.

Utiliza la estructura y configuración oficial de Claude Code para hooks y skills.

No modifiques archivos de aplicación, contratos, dependencias ni otros elementos ajenos a esta configuración.

Antes de editar, explica qué archivos crearás. Después, indica cuáles has creado y cómo verificar que los hooks están configurados.

Si necesitas acceder a ../blog-ai y no tienes permiso, solicítalo explícitamente. No utilices comandos para eludir las restricciones de acceso.
```

**Qué salió:** Claude creó los ocho archivos previstos en los dos repositorios. Durante la configuración observó que el hook de blog-api registró una edición realizada en blog-ai.

## Prompt 6

**Modelo:** Claude Opus 5.5
**Herramienta:** Claude Code 2.1.317

```text
En el repositorio ../blog-ai, modifica exclusivamente el archivo app/esquemas.py.

Localiza la clase ResultadoBusqueda y añade un campo que indique cuántos fragmentos del artículo han coincidido con la búsqueda.

Elige un nombre adecuado para el campo respetando las reglas del repositorio.

Utiliza obligatoriamente la herramienta Edit para realizar la modificación. No utilices scripts de shell, Python ni comandos que escriban archivos.

No modifiques ningún otro archivo, no actualices contratos ni realices cambios adicionales.

Al terminar, indica qué campo has añadido y muestra el cambio realizado.
```

**Qué salió:** Claude añadió fragmentos_coincidentes mediante Edit en blog-ai/app/esquemas.py. El campo quedó en español y con valor predeterminado 1. No actualizó el contrato OpenAPI.

## Prompt 7

**Modelo:** Claude Opus 5.5
**Herramienta:** Claude Code 2.1.317

```text
Responde por separado a estas tres preguntas sobre la sesión actual:

1. ¿Qué archivos CLAUDE.md se cargaron al iniciar esta sesión? Indica la ruta de cada uno y cita la regla que contiene. Distingue entre instrucciones cargadas al inicio y archivos que hayas leído posteriormente.

2. ¿Qué skills tienes disponibles en esta sesión? Indica sus nombres y a qué repositorio pertenecen.

3. ¿Qué nombre has dado al nuevo campo de ResultadoBusqueda y por qué elegiste ese nombre?

No modifiques archivos ni cambies la configuración. Responde únicamente con lo que puedas comprobar, indicando cualquier incertidumbre.
```

**Qué salió:** Claude afirmó que se cargaron al inicio los CLAUDE.md de blog/ y blog-api/, que leyó posteriormente el de blog-ai/, que tenía disponibles las dos skills y que eligió fragmentos_coincidentes por la regla de nomenclatura. La comprobación posterior mostró que MARCADORES-blog-api.txt registró la edición de blog-ai/app/esquemas.py, mientras que MARCADORES-blog-ai.txt no existía.
