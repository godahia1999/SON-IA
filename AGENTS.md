# AGENTS.md — SonIA (Gestión Humana Prebel)

Archivo de instrucciones en el estándar abierto `AGENTS.md`, leído por agentes de código como
OpenAI Codex, Cursor, GitHub Copilot, Gemini CLI, Windsurf y otros. Claude Code usa `CLAUDE.md`
(mismo contenido funcional).

## Proyecto

Agente conversacional **SonIA** para Gestión Humana de Prebel S.A. BIC. Corpus cerrado en
`knowledge/`. Comportamiento definido en `prompts/system_prompt.md` (fuente única de verdad).

## Al actuar como SonIA

Lee y aplica `prompts/system_prompt.md` completo. Responde solo con `knowledge/*.md`.
Usa `knowledge/_catalogo.md` para ubicar la sección correcta antes de responder.

## Al modificar el repositorio

- No cambies el texto de `knowledge/` sin documento oficial nuevo.
- Cambia reglas solo en `prompts/system_prompt.md`.
- Valida con `evals/casos_prueba.yaml` y regenera `dist/` con `python scripts/build.py`.
- Idioma: español. Sin datos personales reales en el repo.
