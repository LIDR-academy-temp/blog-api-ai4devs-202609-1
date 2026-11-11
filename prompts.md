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

## Prompt 

```
**Modelo:** lo ves al arrancar Claude Code
**Herramienta:** Claude Code 2.1.318, terminal de VS Code, sesión en blog-api

  ```
  resume este proyecto
  ```

  Resultado: describió blog-api (AdonisJS 6, puerto 3402, dueño del contenido, contrato fijado con blog-ai) y confirmó que ni blog-api ni blog-ai tenían CLAUDE.md ni carpeta `.claude/`. También propuso un "ejercicio" sacado del README  la plataforma; seguí el de la plataforma.

  ## Prompt 1 — Rotura 1, Paso 1 (bloqueado por auto mode)

  Modelo: <modelo> · Herramienta: Claude Code 2.1.318, terminal de VS C*auto mode activo**

  ```
  Monta la misma estructura mínima de gobierno en dos repositorios hermanos: en este (blog-api) y en ../blog-ai. En cada uno de los dos, tres piezas. Primero, un    CLAUDE.md en la raíz con UNA regla propia de ese repositorio: la de btorio es el dueño del contenido y todo archivo nuevo abre con uncomentario que lo diga; la de blog-ai es que los nombres de campo de su contrato público se escriben en español, nunca en inglés. Segundo, un hook PostToolUse que se dispare con Write y con Edit y añada una línea a un archivo MARCAD en la raíz de ese mismo repositorio, con la fecha, la herramientausada y la ruta del archivo escrito. Que el hook use rutas absolutas, porque va a dispararse sobre archivos que no están en su propio árbol. Tercero, una skill
  trivial llamada marcador-<nombre-del-repo> cuya descripción diga de qes ningún otro archivo de ninguno de los dos repositorios.
  ```

  Resultado: el clasificador del auto mode bloqueó la acción por "Self-Modification". El agente no creó nada y propuso un script en su carpeta temporal, que no
  ejecuté. La respuesta anterior ya terminaba con la línea de la REGLA-og/` estaba cargado.

  ## Prompt 2 — Rotura 1, Paso 1 (reintento en modo manual)

  Modelo: <modelo> · Herramienta: Claude Code 2.1.318, terminal de VS Codo manual

  ```
  Monta la misma estructura mínima de gobierno en dos repositorios hermanos: en este (blog-api) y en ../blog-ai. En cada uno de los dos, tres piezas. Primero, un CLAUDE.md en la raíz con UNA regla propia de ese repositorio: la de btorio es el dueño del contenido y todo archivo nuevo abre con uncomentario que lo diga; la de blog-ai es que los nombres de campo de su contrato público se escriben en español, nunca en inglés. Segundo, un hook PostToolUse que
  se dispare con Write y con Edit y añada una línea a un archivo MARCAD en la raíz de ese mismo repositorio, con la fecha, la herramientausada y la ruta del archivo escrito. Que el hook use rutas absolutas, porque va a dispararse sobre archivos que no están en su propio árbol. Tercero, una skill
  trivial llamada marcador-<nombre-del-repo> cuya descripción diga de qes ningún otro archivo de ninguno de los dos repositorios.
  ```

  Resultado: creó los seis archivos, aprobados uno por uno: CLAUDE.md, `.claude/settings.json` y `.claude/skills/marcador-<repo>/SKILL.md` en cada repositorio. El hook de blog-api se activó en plena sesión y registró escrituras sobrié los dos marcadores antes del Paso 4 para medir limpio.
                                                                                                                                                                 ## Prompt 3 — Rotura 2, Paso 2 (lanzado fuera de orden)
                                                                                                                                                                 Modelo: <modelo> · Herramienta: Claude Code 2.1.318, terminal de VS Cin `--add-dir`)
                                                                                                                                                                 ```
  En el repositorio blog-ai, renombra el campo `puntuacion` de la clase ResultadoBusqueda a `score`. Son exactamente tres sitios y no hay más: la declaración delcampo en app/esquemas.py, el sitio donde se construye ese objeto en ael sitio de app/main.py donde se lee para rellenar la Fuente quedevuelve /preguntar. No toques la clase Fuente, no toques los alias de la consulta SQL, no regeneres el contrato de contrato/openapi.json, y no toques nada de blog-api ni de blog-web: quiero ver qué pasa cuando el cambio se qued, que es lo que pasa de verdad.
  ```

  Resultado: me salté los Pasos 3 a 6 de la Rotura 1. El agente no hizo el cambio porque leyó por iniciativa propia el CLAUDE.md de blog-ai (regla del español) y me
  preguntó cómo seguir.

  ## Prompt 4 — Detener el prompt anterior

  Modelo: <modelo> · Herramienta: Claude Code 2.1.318, terminal de VS C

  ```
  No hagas ningún cambio por ahora. Lo dejamos aquí.
  ```

  Resultado: no se modificó ningún archivo.

  ## Prompt 5 — Rotura 1, Paso 4

  Modelo: <modelo> · Herramienta: Claude Code 2.1.318, terminal de VS Capi arrancada con `claude --add-dir ../blog-ai`, modo manual

  ```
  Añade a la clase ResultadoBusqueda de ../blog-ai/app/esquemas.py un campo nuevo que indique cuántos fragmentos del post han coincidido con la búsqueda. Edita solo ese archivo, y edítalo con la herramienta de edición de archivos, nun Cuando termines, dime tres cosas por separado: primero, qué archivos CLAUDE.md se te han cargado automáticamente al arrancar, citando de cada uno la regla que contiene; segundo, qué skills tienes disponibles, listando sus nombres; ytercero, qué nombre le has puesto al campo y por qué ese y no otro.
  ```                                                                                                                                                                
  Resultado: editó con la herramienta Edit. Dijo que cargó `blog/CLAUDE.md` (REGLA-PADRE) y `blog-api/CLAUDE.md`, y que el de blog-ai no se cargó solo y lo leyó él. Listó `marcador-blog-api` y `marcador-blog-ai`. Nombró el campo `fragspañol, por la regla de blog-ai que leyó por iniciativa propia.Marcadores: el de blog-api registró `Edit /Users/brenda/blog/blog-ai/app/esquemas.py` y el de blog-ai no existe. Después revertí `esquemas.py`.

  ## Prompt 6 — Rotura 2, Paso 2 (práctica opcional)

  Modelo: <modelo> · Herramienta: Claude Code 2.1.318, terminal de VS Code, sesión en blog-api con `--add-dir ../blog-ai`, modo manual

  ```
  En el repositorio blog-ai, renombra el campo `puntuacion` de la clasee`. Son exactamente tres sitios y no hay más: la declaración delcampo en app/esquemas.py, el sitio donde se construye ese objeto en app/servicios/indice.py, y el sitio de app/main.py donde se lee para rellenar la Fuente que
  devuelve /preguntar. No toques la clase Fuente, no toques los alias dneres el contrato de contrato/openapi.json, y no toques nada deblog-api ni de blog-web: quiero ver qué pasa cuando el cambio se queda dentro de su repositorio, que es lo que pasa de verdad.
  ```

  Resultado: esta vez lo hizo sin preguntar, reconociendo que viola la  respondió 200, las 21 pruebas de blog-api pasaron y el build deblog-web compiló, mientras blog-api devolvía `puntuacion: null` y `score` con el valor. Los dos gates de contrato salieron con exit=1 (la versión seguía en 1.0.0; los delató la huella). Con `CONTRATO_ESTRICTO=true`, blog-api devolviDO`. Revertí el cambio y los contratos volvieron a coincidir (200 con `puntuacion`).

  ---

  ## Anexo — Comandos de shell (`!` en Claude Code) usados para comprobar

  - Tres historiales: `!(cd .. && for d in blog-api blog-web blog-ai; do printf '%-10s ' "$d"; git -C "$d" log --oneline -1; done)`
  - Seis archivos creados: `!(cd .. && find blog-api/CLAUDE.md blog-ai/ blog-ai/.claude -type f 2>/dev/null | sort)`
  - Vaciar marcadores antes de medir: `!(cd .. && rm -f blog-api/MARCADORES-blog-api.txt blog-ai/MARCADORES-blog-ai.txt && echo "marcadores limpios")`
  - Leer los dos marcadores: `!(cd .. && echo "--- marcador de blog-apiORES-blog-api.txt 2>/dev/null || echo "(no existe)"; echo "---marcador de blog-ai ---"; cat blog-ai/MARCADORES-blog-ai.txt 2>/dev/null || echo "(NO EXISTE)")`
  - Revertir la Rotura 1: `!(cd .. && (cd blog-ai && git checkout -- aps --short))`
  - Rotura 2: `curl` a `/buscar`, pruebas y build de los repositorios no tocados, `jq` de `puntuacion` contra `score`, gates `generar_openapi.py --verificar` y `node
  ace contrato:verificar`, `curl` con modo estricto y restauración con  archivos.

Aquí está el resumen con tu estructura. Solo veo esta sesión, que emprompts 0 a 4 los he copiado tal cual de tu borrador, sin podercomprobarlos, y en ellos he dejado <modelo>. En esta sesión hubo además dos prompts que tu borrador no recoge: el de «corrobora que estes el blog-api» y el comando
de .env. Los he incluido en su orden, así que la numeración cambia de

---

Prompt 0 — Preparación: comprobar que el agente arranca en blog-api

Modelo: <modelo> · Herramienta: Claude Code 2.1.318, terminal de VS C

resume este proyecto

Resultado: describió blog-api (AdonisJS 6, puerto 3402, dueño del conn blog-ai) y confirmó que ni blog-api ni blog-ai tenían CLAUDE.md nicarpeta .claude/. También propuso un "ejercicio" sacado del README que no coincidía con el de la plataforma; seguí el de la plataforma.

Prompt 1 — Rotura 1, Paso 1 (bloqueado por auto mode)

Modelo: <modelo> · Herramienta: Claude Code 2.1.318, terminal de VS Code, sesión en blog-api, auto mode activo

Monta la misma estructura mínima de gobierno en dos repositorios hermanos: en este (blog-api) y en ../blog-ai. En cada uno de los dos, tres piezas. Primero, un
CLAUDE.md en la raíz con UNA regla propia de ese repositorio: la de btorio es el dueño del contenido y todo archivo nuevo abre con uncomentario que lo diga; la de blog-ai es que los nombres de campo de su contrato público se escriben en español, nunca en inglés. Segundo, un hook PostToolUse que se
dispare con Write y con Edit y añada una línea a un archivo MARCADORE la raíz de ese mismo repositorio, con la fecha, la herramienta usada y la ruta del archivo escrito. Que el hook use rutas absolutas, porque va a dispararse sobre archivos que no están en su propio árbol. Tercero, una skill trivial
llamada marcador-<nombre-del-repo> cuya descripción diga de qué reposn otro archivo de ninguno de los dos repositorios.

Resultado: el clasificador del auto mode bloqueó la acción por "Self-o creó nada y propuso un script en su carpeta temporal, que noejecuté. La respuesta anterior ya terminaba con la línea de la REGLA-PADRE: el CLAUDE.md de blog/ estaba cargado.

Prompt 2 — Rotura 1, Paso 1 (reintento en modo manual)

Modelo: <modelo> · Herramienta: Claude Code 2.1.318, terminal de VS Code, sesión en blog-api, modo manual

(mismo texto que el Prompt 1)

Resultado: creó los seis archivos, aprobados uno por uno: CLAUDE.md, .claude/settings.json y .claude/skills/marcador-<repo>/SKILL.md en cada repositorio. El hook de
blog-api se activó en plena sesión y registró escrituras sobre archivos marcadores antes del Paso 4 para medir limpio.

Prompt 3 — Rotura 2, Paso 2 (lanzado fuera de orden)

Modelo: <modelo> · Herramienta: Claude Code 2.1.318, terminal de VS Cin --add-dir)

(mismo texto que el Prompt 7)

Resultado: me salté los Pasos 3 a 6 de la Rotura 1. El agente no hizo iniciativa propia el CLAUDE.md de blog-ai (regla del español) y mepreguntó cómo seguir.

Prompt 4 — Detener el prompt anterior

Modelo: <modelo> · Herramienta: Claude Code 2.1.318, terminal de VS Code, sesión en blog-api

No hagas ningún cambio por ahora. Lo dejamos aquí.

Resultado: no se modificó ningún archivo.

Prompt 5 — Rotura 1, Paso 4

Modelo: Claude Opus 5.5 (claude-opus-5-5) · Herramienta: Claude Code 2.1.318, terminal de VS Code, sesión nueva en blog-api arrancada con claude --add-dir
../blog-ai, modo manual

Añade a la clase ResultadoBusqueda de ../blog-ai/app/esquemas.py un cntos fragmentos del post han coincidido con la búsqueda. Edita soloese archivo, y edítalo con la herramienta de edición de archivos, nunca con un script de shell. Cuando termines, dime tres cosas por separado: primero, qué archivos
CLAUDE.md se te han cargado automáticamente al arrancar, citando de cene; segundo, qué skills tienes disponibles, listando sus nombres; ytercero, qué nombre le has puesto al campo y por qué ese y no otro.

Resultado:
- La edición: editó solo esquemas.py y lo hizo con la herramienta Edi
- Los CLAUDE.md: dijo que se cargaron blog/CLAUDE.md (REGLA-PADRE) y blog-api/CLAUDE.md (dueño del contenido). El de blog-ai no se cargó solo; lo leyó por iniciativa
  propia antes de editar.
- Las skills: listó marcador-blog-api y marcador-blog-ai junto a las de los plugins.
- El campo: lo llamó fragmentos_coincidentes: int = Field(default=1, ñol por la regla de blog-ai y siguió la convención fragmentos /fragmentos_indexados del archivo. Le puso valor por defecto porque indice.py construye el objeto sin ese campo, y avisó de que faltaba calcularlo y regenerar el
  contrato.
- Los marcadores: el de blog-api registró Edit /Users/brenda/blog/blog-ai/app/esquemas.py y el de blog-ai no existe. Los hooks salen del proyecto donde arranca la
  sesión, no del repo del archivo editado.

Después revertí esquemas.py.

Prompt 6 — Comprobar el directorio de trabajo

Modelo: Claude Opus 5.5 · Herramienta: Claude Code 2.1.318, terminal -api con --add-dir ../blog-ai, modo manual

corrobora que estes el blog-api

Resultado: reconoció que no estaba en blog-api. La shell se había que/blog-ai, en la rama s7/start, por un cd de un grep anterior. Se movió y confirmó /Users/brenda/blog/blog-api en la rama frontera-bl.                                                                                                       
Prompt 7 — Rotura 2, Paso 2 (práctica opcional)                                                                                                                      
Modelo: Claude Opus 5.5 · Herramienta: Claude Code 2.1.318, terminal de VS Code, sesión en blog-api con --add-dir ../blog-ai, modo manual                            
En el repositorio blog-ai, renombra el campo `puntuacion` de la clase ResultadoBusqueda a `score`. Son exactamente tres sitios y no hay más: la declaración del campo  app/esquemas.py, el sitio donde se construye ese objeto en app/serio de app/main.py donde se lee para rellenar la Fuente que devuelve/preguntar. No toques la clase Fuente, no toques los alias de la consulta SQL, no regeneres el contrato de contrato/openapi.json, y no toques nada de blog-api ni de  og-web: quiero ver qué pasa cuando el cambio se queda dentro de su  pasa de verdad.
                                                                                                                                                                      sultado: esta vez lo hizo sin preguntar. Cambió 3 archivos con una que violaba la regla del español de blog-ai, que siguió porque lapetición era explícita. Al comprobarlo con !:                                                                                                                         Lo que siguió en verde: blog-ai respondió 200, las 21 pruebas de blde blog-web compiló.
- Lo que se rompió: blog-api devolvía puntuacion: null y score con el valor (0.6735 y 0.5455).                                                                        Los dos gates de contrato: salieron con exit=1. La versión seguía ella, 8190a65ab0f65d7c fijada frente a 944cd887122e6997 viva.
                                                                                                                                                                       agente avisó de que regenerar y copiar el contrato solo daría por
                                                                                                                                                                      ompt 8 — Activar el modo estricto del contrato en blog-api
                                                                                                                                                                      delo: Claude Opus 5.5 · Herramienta: Claude Code 2.1.318, terminal -api con --add-dir ../blog-ai, modo manual
                                                                                                                                                                       ~/blog/blog-api && grep -v '^CONTRATO_ESTRICTO=' .env > .env.tmp &true' >> .env.tmp && mv .env.tmp .env && grep CONTRATO_ESTRICTO .env
                                                                                                                                                                      sultado:
- El comando: lo ejecutó el agente y .env quedó con CONTRATO_ESTRICTO=true.                                                                                           Con el modo estricto: blog-api devolvió 502 E_CONTRATO_INCUMPLIDO,  resultados[0..1].puntuacion.
- Al revertir: revertí los tres archivos, los dos gates volvieron a pasar con la huella 8190a65ab0f65d7c y /buscar volvió a dar 200 con puntuacion, todavía en modo   estricto.
                                                                                                                                                                      NTRATO_ESTRICTO=true sigue en .env.
                                                                                                                                                                      -
                                                                                                                                                                      exo — Comandos de shell (! en Claude Code) usados para comprobar
                                                                                                                                                                      Tres historiales: !(cd .. && for d in blog-api blog-web blog-ai; do -C "$d" log --oneline -1; done)
- Seis archivos creados: !(cd .. && find blog-api/CLAUDE.md blog-ai/CLAUDE.md blog-api/.claude blog-ai/.claude -type f 2>/dev/null | sort)                            Vaciar marcadores antes de medir: !(cd .. && rm -f blog-api/MARCADOARCADORES-blog-ai.txt && echo "marcadores limpios")
- Leer los dos marcadores: !(cd .. && echo "--- marcador de blog-api ---"; cat blog-api/MARCADORES-blog-api.txt 2>/dev/null || echo "(no existe)"; echo "--- marcador de blog-ai ---"; cat blog-ai/MARCADORES-blog-ai.txt 2>/dev/null ||
- Revertir la Rotura 1: !(cd .. && (cd blog-ai && git checkout -- app/esquemas.py && git status --short))
- Rotura 2, búsqueda a través de blog-api: !curl -s -X POST localhostype: application/json' -d '{"consulta":"modo oscuro","limite":2}' |python3 -m json.tool
- Rotura 2, los repos no tocados: !(cd .. && curl -s -o /dev/null -w %{http_code}\n' -X POST localhost:8402/buscar …; (cd blog-api && nodeace test 2>&1 | tail -3); (cd blog-web && npm run build 2>&1 | tail -2))                                                                                        Rotura 2, puntuacion frente a score: !curl -s -X POST localhost:340.resultados[] | "\(.titulo)\n  puntuacion -> \(.puntuacion) …\n  score -> \(.score) …"'                                                                                                                                                Rotura 2, los gates: !(cd .. && (cd blog-ai && .venv/bin/python scrverificar); echo "exit=$?"; (cd blog-api && node acecontrato:verificar); echo "exit=$?")                                                                                                                            Rotura 2, modo estricto: !(curl -s -o /tmp/respuesta.json -w 'HTTP calhost:3402/buscar … ; python3 -m json.tool /tmp/respuesta.json)
- Restaurar la Rotura 2: !(cd .. && (cd blog-ai && git checkout -- app/esquemas.py app/servicios/indice.py app/main.py); sleep 5; (cd blog-ai && .venv/bin/python scripts/generar_openapi.py --verificar); (cd blog-api && node ace c2))

REGLA-PADRE aplicada: gobierno desde fuera de todos los repositorios.