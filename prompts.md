# Prompts

Registro de los prompts utilizados en el Laboratorio 7 — Blog Polirepo, Módulo 7: AI For Polyrepo Projects.

Los prompts se presentan en orden cronológico, conservando su texto original recuperado del historial de sesiones de Claude Code.

---

## Prompt 1 — Verificación inicial de blog-ai

**Modelo:** claude-opus-5-5
**Herramienta:** Claude Code
**Repositorio:** blog-ai

**Prompt original:**

```text
Resume brevemente el propósito de este repositorio y sus principales componentes.

Ejecuta el comando `pwd` para comprobar el directorio desde el que estás trabajando.

No modifiques archivos, no instales dependencias y no ejecutes comandos que cambien el estado del proyecto.
```

**Qué salió:** Comprobación inicial del repositorio y su directorio de trabajo, sin modificar archivos.

## Prompt 2 — Verificación inicial de blog-api

**Modelo:** claude-opus-5-5
**Herramienta:** Claude Code
**Repositorio:** blog-api

**Prompt original:**

```text
Resume brevemente el propósito de este repositorio y sus principales componentes.

Para comprobar que puedes utilizar herramientas, ejecuta el comando `pwd` e indica el directorio de trabajo que devuelve.

No modifiques archivos, no instales dependencias y no ejecutes comandos que cambien el estado del proyecto.
```

**Qué salió:** Comprobación inicial del repositorio y su directorio de trabajo, sin modificar archivos.

## Prompt 3 — Configuración de guardarraíles

**Modelo:** claude-opus-5-5
**Herramienta:** Claude Code
**Repositorio de inicio:** blog-api

**Prompt original:**

```text
Trabajamos en el ejercicio oficial del Módulo 7, Blog Polirepo.

Tu directorio de trabajo es blog-api y el repositorio hermano blog-ai está en ../blog-ai.

Objetivo: configurar tres mecanismos de gobierno en cada repositorio, sin modificar el código de la aplicación ni otros archivos.

**1. En blog-api:**
- Crea un CLAUDE.md en la raíz con una única regla propia: este repositorio es el dueño del contenido y todo archivo nuevo debe comenzar con un comentario que indique esa propiedad.
- Configura un hook PostToolUse para las herramientas Write y Edit. Debe añadir una línea a MARCADORES-blog-api.txt, en la raíz de blog-api, indicando fecha, herramienta utilizada y ruta del archivo modificado.
- Crea una skill sencilla llamada marcador-blog-api, cuya descripción indique claramente que pertenece a blog-api.

**2. En blog-ai:**
- Crea un CLAUDE.md en la raíz con una única regla propia: los nombres de los campos del contrato público deben estar escritos en español, nunca en inglés.
- Configura un hook PostToolUse para las herramientas Write y Edit. Debe añadir una línea a MARCADORES-blog-ai.txt, en la raíz de blog-ai, indicando fecha, herramienta utilizada y ruta del archivo modificado.
- Crea una skill sencilla llamada marcador-blog-ai, cuya descripción indique claramente que pertenece a blog-ai.

**Restricciones:**
- Utiliza rutas absolutas en los hooks, tanto para identificar el repositorio del marcador como para registrar el archivo modificado, incluyendo archivos situados fuera del repositorio.
- Utiliza la estructura y configuración de Claude Code compatible con la versión instalada.
- No modifiques código fuente, pruebas, dependencias, contratos ni archivos ajenos a los mecanismos solicitados.
- No instales herramientas ni cambies el modo de permisos.
- No utilices scripts de shell para eludir restricciones de acceso a directorios.
- Si necesitas autorización para acceder a ../blog-ai, solicítala. Si no puedes acceder, informa de la limitación sin sustituirla por otra solución.

Al terminar, informa qué archivos creaste o modificaste en cada repositorio y qué mecanismos quedaron configurados. No realices todavía el experimento sobre ResultadoBusqueda.
```

**Qué salió:** Claude Code creó las instrucciones `CLAUDE.md`, los hooks `PostToolUse` y las skills `marcador-blog-api` y `marcador-blog-ai`. El hook de `blog-api` registró operaciones de escritura realizadas durante la configuración.

## Prompt 4 — Revisión de guardarraíles sin prueba adicional

**Modelo:** claude-opus-5-5
**Herramienta:** Claude Code
**Repositorio de inicio:** blog-api

**Prompt original:**

```text
No ejecutes todavía la prueba dinámica del hook mediante `bash -c`.

Primero revisa y muestra el contenido de `.claude/settings.json` de ambos repositorios, indicando los comandos configurados para `PostToolUse`.

Comprueba la validez del JSON y consulta el estado Git de ambos repositorios utilizando únicamente operaciones de lectura.

No ejecutes los hooks manualmente, no crees archivos de prueba y no modifiques la configuración existente.

Informa también qué archivos has creado hasta ahora en `blog-api` y `blog-ai`.
```

**Qué salió:** Se revisaron las configuraciones de los hooks y se comprobó la validez de los archivos JSON, sin ejecutar la prueba dinámica adicional ni modificar la configuración.

## Prompt 5 — Experimento de frontera sobre ResultadoBusqueda

**Modelo:** claude-opus-5-5
**Herramienta:** Claude Code
**Repositorio de inicio:** blog-api
**Directorio adicional:** ../blog-ai
**Modo de permisos:** Manual mode

**Prompt original:**

```text
Trabajamos en la Parte A del ejercicio oficial Blog Polirepo del Módulo 7.

Desde esta sesión iniciada en blog-api, con blog-ai añadido mediante --add-dir, modifica exclusivamente el archivo ../blog-ai/app/esquemas.py.

En la clase ResultadoBusqueda, añade un campo que indique cuántos fragmentos del artículo han coincidido con la búsqueda.

Restricciones:
- Modifica únicamente ../blog-ai/app/esquemas.py.
- Utiliza la herramienta de edición de archivos Edit o Write de Claude Code. No utilices Bash, Python, sed ni ningún script para realizar la modificación.
- No modifiques contratos, pruebas ni otros archivos.
- No crees ni ajustes hooks, skills o archivos de instrucciones.
- Mantén Manual mode y solicita autorización cuando corresponda.

Una vez realizada la modificación, responde por separado estas tres preguntas:

1. ¿Qué archivos CLAUDE.md se cargaron al iniciar esta sesión? Identifica cada archivo y cita su regla.
2. ¿Qué skills tienes disponibles en esta sesión? Indica sus nombres.
3. ¿Qué nombre diste al nuevo campo de ResultadoBusqueda y por qué lo elegiste?

Indica también si no pudiste completar alguna parte. No intentes corregir ni ampliar los guardarraíles existentes.
```

**Qué salió:** Claude Code utilizó `Edit` para incorporar `fragmentos_coincidentes` en `blog-ai/app/esquemas.py`. Declaró haber cargado los `CLAUDE.md` de la carpeta padre y de `blog-api`, pero no el de `blog-ai`. Informó que estaban disponibles ambas skills. El archivo `MARCADORES-blog-api.txt` registró la edición, mientras que `MARCADORES-blog-ai.txt` no se generó. El cambio experimental fue revertido después de comprobar los resultados.
