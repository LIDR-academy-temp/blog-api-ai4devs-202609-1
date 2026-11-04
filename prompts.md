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

**Modelo:** Opus 5.5 High
**Herramienta:** Claude Code

```
Resume brevemente qué hace este repositorio, cuál es su tecnología principal y cómo se arranca. Puedes consultar los archivos necesarios, pero no modifiques nada.
```

**Qué salió:** Claude respondió correctamente desde blog-api y pudo consultar los archivos del proyecto.


## Prompt 2

**Modelo:** Opus 5.5 High
**Herramienta:** Claude Code

```
Resume brevemente qué hace este repositorio, cuál es su tecnología principal y cómo se arranca. Puedes consultar los archivos necesarios, pero no modifiques nada.
```

**Qué salió:** Claude respondió correctamente desde blog-ai y pudo consultar los archivos del proyecto.



## Prompt 3

**Modelo:** Opus 5.5 High
**Herramienta:** Claude Code

```
Vamos a preparar un experimento del Módulo 7 sobre el alcance de las instrucciones, hooks y skills de Claude Code en un sistema polirepo.

Trabaja desde este repositorio (blog-api) y prepara los siguientes elementos tanto aquí como en el repositorio hermano ../blog-ai.

1. INSTRUCCIONES
Crea un CLAUDE.md en la raíz de cada repositorio, con una única regla propia:
- blog-api: "Este repositorio es el dueño del contenido y todo archivo nuevo debe empezar con un comentario que lo indique".
- blog-ai: "Los nombres de los campos del contrato público deben escribirse en español, nunca en inglés".

No copies las reglas de un repositorio al otro ni modifiques el CLAUDE.md de la carpeta padre.

2. HOOKS
Configura en cada repositorio un hook PostToolUse que se ejecute tras utilizar las herramientas Write y Edit.

Cada ejecución debe añadir una línea al archivo de marcadores de su propio repositorio:
- blog-api/MARCADORES-blog-api.txt
- blog-ai/MARCADORES-blog-ai.txt

Cada línea debe registrar:
- Fecha y hora.
- Nombre de la herramienta utilizada (Write o Edit).
- Ruta absoluta del archivo modificado.

Utiliza rutas absolutas en la configuración o ejecución del hook. El registro debe funcionar también cuando el archivo modificado esté fuera del repositorio al que pertenece el hook. No restrinjas el registro a archivos de su propio repositorio.

3. SKILLS
Crea una skill sencilla en cada repositorio:
- marcador-blog-api, con una descripción que identifique claramente blog-api.
- marcador-blog-ai, con una descripción que identifique claramente blog-ai.

Utiliza la estructura estándar de skills de Claude Code.

RESTRICCIONES
- No modifiques código de aplicación, contratos, dependencias, Makefiles ni archivos .env.
- No cambies ningún archivo que no sea necesario para crear estas tres piezas.
- Utiliza preferentemente las herramientas Write y Edit para crear o modificar los archivos.
- Si necesitas autorización para acceder a ../blog-ai, solicítala. No cambies de estrategia silenciosamente.
- No ejecutes pruebas que alteren el código de la aplicación.

Al terminar, indica qué archivos has creado o modificado en cada repositorio, dónde están configurados los hooks y qué has podido verificar realmente. Distingue entre configuración creada y funcionamiento todavía no comprobado.
```

**Qué salió:** Se crearon las instrucciones, hooks y skills en ambos repositorios. El hook de blog-api registró una escritura externa; el de blog-ai no se observó en ejecución.


## Prompt 4

**Modelo:** Opus 5.5 High
**Herramienta:** Claude Code

```
Estamos realizando un experimento sobre el alcance de las instrucciones, hooks y skills de Claude Code en un sistema polirepo.

Desde esta sesión iniciada en blog-api, modifica exclusivamente el archivo ../blog-ai/app/esquemas.py.

En la clase ResultadoBusqueda, añade un campo que indique cuántos fragmentos del artículo han coincidido con la búsqueda.

Restricciones:
- Modifica únicamente ../blog-ai/app/esquemas.py.
- Utiliza la herramienta Edit para realizar el cambio.
- No utilices Bash, scripts de Python, sed ni otros mecanismos para editar archivos.
- No modifiques otros archivos ni intentes corregir o reconfigurar los hooks, instrucciones o skills.
- No crees commits.

Después de realizar la modificación, responde por separado a estas tres preguntas:

1. ¿Qué archivos CLAUDE.md se cargaron al iniciar esta sesión? Cita la regla de cada uno y distingue los archivos cargados automáticamente de los que hayas consultado después.
2. ¿Qué skills tienes disponibles en esta sesión?
3. ¿Qué nombre has dado al campo nuevo y por qué lo has elegido?

Describe únicamente lo que hayas podido observar; no supongas que una regla o un hook se ha aplicado por el simple hecho de existir.
```

**Qué salió:** La ejecución se interrumpió al denegar la lectura de un archivo de estado personal de Sinapsis; fue necesario enviar un prompt de continuación.

## Prompt 4.1

**Modelo:** Opus 5.5 High
**Herramienta:** Claude Code

```
La lectura de ~/.claude/skills/_operator-state.json ha sido denegada porque no es necesaria para este experimento.

Continúa ejecutando el encargo anterior, sin consultar ese archivo ni otros archivos personales de estado de las skills.

Limítate a modificar ../blog-ai/app/esquemas.py mediante la herramienta Edit, añadiendo a ResultadoBusqueda el campo solicitado. Mantén todas las restricciones originales.

Después responde a las tres preguntas del prompt anterior sobre los CLAUDE.md cargados al inicio, las skills disponibles y el nombre elegido para el campo.

Si no puedes determinar algún dato con certeza, indícalo expresamente. No necesitas consultar archivos personales para completar la tarea.
```

**Qué salió:** La edición se completó mediante Edit. Claude informó de las instrucciones y skills disponibles; los marcadores confirmaron la ejecución del hook de blog-api sobre blog-ai.