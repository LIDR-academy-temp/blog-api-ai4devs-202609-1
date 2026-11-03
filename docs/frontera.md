# Respuesta a la primera pregunta
## 1. Archivos CLAUDE.md cargados al iniciar la sesión

  | Archivo | Nivel | Regla que contiene |
  |---|---|---|
  | `/home/shey/CURSO-LIDR/blog/CLAUDE.md` | Carpeta padre, fuera de todos los repositorios | **REGLA-PADRE**: toda respuesta termina con la línea literal «REGLA-PADRE aplicada: gobierno desde fuera de todos los repositorios.» |
  | `/home/shey/CURSO-LIDR/blog/blog-api/CLAUDE.md` | Repositorio `blog-api`, el directorio de trabajo principal | Todo archivo nuevo que se cree en `blog-api` debe empezar con un comentario como `// blog-api: este repositorio es el dueño del contenido.` |

  No se cargó ningún `CLAUDE.md` de `blog-ai`, aunque está añadido como directorio de trabajo adicional. Tampoco comprobé si existe uno. La regla de `blog-api` no se aplicó al cambio porque no creé ningún archivo y solo edité uno en `blog-ai`.
No se cargó ningún `CLAUDE.md` de `blog-ai`, aunque está añadido como directorio de trabajo adicional. Tampoco comprobé si existe uno. La regla de `blog-api` no se aplicó al cambio porque no creé ningún archivo y solo edité uno en `blog-ai`.

## 2. Skills disponibles

| Origen | Skills |
|---|---|
| Del proyecto (repositorios del blog) | `marcador-blog-api`, `marcador-blog-ai` |
| Configuración y uso de Claude Code | `update-config`, `keybindings-help`, `fewer-permission-prompts`, `plugin-authoring`, `init`, `loop`, `schedule`, `run` |
| Revisión de código | `code-review`, `simplify`, `security-review` |
| Desarrollo con la API de Claude | `claude-api` |
| Visualización | `dataviz` |
| Navegador y escritorio | `claude-in-chrome`, `anthropic-skills:chrome-browser`, `anthropic-skills:built-in-browser`, `anthropic-skills:computer-use` |
| Documentos y archivos | `anthropic-skills:docs`, `anthropic-skills:docx`, `anthropic-skills:pdf`, `anthropic-skills:pptx`, `anthropic-skills:xlsx`, `anthropic-skills:google-workspace` |
| Otras | `anthropic-skills:deep-research`, `anthropic-skills:skill-creator`, `anthropic-skills:import-memory`, `anthropic-skills:morning` |

Las dos skills de marcador aparecen a la vez en la lista. Esa lista no indica desde qué carpeta se cargó cada una.

## 3. Nombre del campo y por qué

| Aspecto | Decisión | Motivo |
|---|---|---|
| Nombre | `fragmentos_coincidentes` | Sigue el estilo del archivo: español, snake_case, sin tildes (como `fragmentos_indexados` o `motivos_omision`). Además dice exactamente qué cuenta: los fragmentos del artículo que coincidieron con la búsqueda. |
| Tipo | `int` | Es un recuento. |
| Valor por defecto | `1` | Solo podía modificar ese archivo, y el código que crea los resultados aún no rellena el campo. Sin valor por defecto, ese código fallaría. Además, si un artículo aparece en los resultados es porque coincidió al menos un fragmento. |
| Validación | `ge=1` | Un resultado con 0 fragmentos coincidentes no tendría sentido. |
| Pendiente | Regenerar `contrato/openapi.json` | El archivo dice que renombrar o añadir campos cambia el contrato que usa `blog-api`. |

REGLA-PADRE aplicada: gobierno desde fuera de todos los repositorios.

# Respuesta a la segunda pregunta Qué encontraste en cada archivo de marcadores y qué indica sobre dónde se ejecuta cada guardarraíl.

Ejecute : cat blog-api/MARCADORES-blog-api.txt

2026-11-03T17:23:41+01:00	Edit	/home/shey/CURSO-LIDR/blog/blog-api/prompts.md
2026-11-03T17:34:16+01:00	Edit	/home/shey/CURSO-LIDR/blog/blog-ai/app/esquemas.py

Ejecute ; cat blog-ai/MARCADORES-blog-ai.txt

cat: blog-ai/MARCADORES-blog-ai.txt: No existe el archivo o el directorio

Al arrancar desde el proyecto blog-api solo cargó el claude.md de la carpeta blog (principal) y la del propio proyecto donde abrí la sesion de claude. El claude.md del repo blog-ai no se cargó.

Al indicarle que modificar un fichero del repo añadido (claude --add-dir ../blog-ai) se ejecutó el hook de blog-api y guardó en el fichero de marcadores MARCADORES-blog-api.txt el fichero esquemas.py del repo blog-ai, y no se ejecuto el hook PostToolUse que hay dentro del repo de blog-ai. 

Conclusión: aunque Claude las cargue en la sesion y estén disponibles, no se puede garantizar que los reglas definidas en un repo añadido se ejecuten dentro de una sesión arrancada



