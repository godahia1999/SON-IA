# SonIA — Agente de Gestión Humana de Prebel

Este repositorio contiene el agente **SonIA** en formato portable. Claude Code lee este archivo
automáticamente al abrir la carpeta.

## Qué es este proyecto

- Chatbot de Gestión Humana para **Prebel S.A. BIC** (reto empresarial EstudIA, capa 2).
- Destino final: **WhatsApp** (Meta Cloud API) desplegado en **servidor on-premise** de Prebel.
- Corpus cerrado: solo responde con `knowledge/*.md`.

## Mapa del repositorio

| Ruta | Para qué sirve |
|------|----------------|
| `prompts/system_prompt.md` | Fuente única de verdad del comportamiento (tono, reglas, ejemplos) |
| `knowledge/` | Base de conocimiento (4 archivos .md, contenido literal de Prebel) |
| `knowledge/_catalogo.md` | Índice tema → archivo → sección, y directorio de contactos |
| `agent.yaml` | Especificación agnóstica (modelo, temperatura, mensajes fijos, canales) |
| `.claude/skills/sonia-gestion-humana/` | Skill para Claude Code / Claude.ai |
| `.claude/agents/sonia.md` | Subagente para probar SonIA dentro de Claude Code |
| `.claude/commands/probar-sonia.md` | Comando `/probar-sonia` que corre los casos de prueba |
| `evals/casos_prueba.yaml` | Casos de prueba con respuesta esperada |
| `scripts/build.py` | Genera `dist/` (prompt único, skill empaquetada) |
| `scripts/chat_api.py` | Ejemplo de chat por API de Claude (base para WhatsApp) |
| `docs/` | Guía de migración por plataforma y notas para el equipo |

## Comportamiento del agente

Cuando actúes **como SonIA** (por ejemplo, si el usuario dice "responde como SonIA" o usa el
subagente), sigue estrictamente:

@prompts/system_prompt.md

y responde solo con el contenido de `knowledge/`.

## Reglas para mantener el repositorio

1. **No edites el contenido de `knowledge/` sin un documento oficial nuevo de Gestión Humana.**
   Si llega una versión nueva: reemplaza el archivo, actualiza `version` en el frontmatter y en
   `knowledge/_catalogo.md`, y anota el cambio en `docs/notas_para_el_equipo.md`.
2. El comportamiento se cambia **solo** en `prompts/system_prompt.md`; los demás archivos lo
   referencian. No dupliques reglas.
3. Después de cualquier cambio: corre `/probar-sonia` y luego `python scripts/build.py`.
4. Idioma de trabajo y de respuesta: **español**.
5. No subas datos personales de colaboradores al repositorio ni a los casos de prueba.
