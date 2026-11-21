# SonIA · Asistente de Gestión Humana de Prebel

Paquete portable del agente SonIA. La estructura sigue las convenciones de **Claude Code**
(`CLAUDE.md`, `.claude/skills`, `.claude/agents`, `.claude/commands`) y además incluye
`AGENTS.md` y `agent.yaml` para que funcione en cualquier otra plataforma.

## Estructura

```
sonia-prebel/
├── CLAUDE.md                     # Instrucciones que Claude Code lee solo
├── AGENTS.md                     # Mismo propósito para Codex, Cursor, Copilot, Gemini CLI
├── agent.yaml                    # Especificación agnóstica (modelo, mensajes fijos, canales)
├── prompts/
│   └── system_prompt.md          # ★ Fuente única de verdad del comportamiento
├── knowledge/                    # ★ Base de conocimiento (texto oficial de Prebel)
│   ├── _catalogo.md              #   Índice tema→sección + directorio de contactos
│   ├── 01_vinculacion_y_nomina.md
│   ├── 02_creditos.md
│   ├── 03_auxilios_y_beneficios.md
│   └── 04_glosario_business_partner.md
├── .claude/
│   ├── skills/sonia-gestion-humana/SKILL.md
│   ├── agents/sonia.md           # Subagente para pruebas
│   └── commands/probar-sonia.md  # /probar-sonia
├── evals/casos_prueba.yaml       # 15 casos de prueba
├── scripts/
│   ├── build.py                  # Genera dist/
│   └── chat_api.py               # Chat por API (base del webhook de WhatsApp)
├── dist/                         # Generado: prompt único, skill .zip, instrucciones GPT
└── docs/
    ├── guia_migracion_plataformas.md
    └── notas_para_el_equipo.md
```

## Inicio rápido

```bash
# Claude Code
cd sonia-prebel && claude
> /probar-sonia
> usa el agente sonia: ¿qué necesito para el auxilio de matrimonio?

# Generar entregables para otras plataformas
python scripts/build.py

# Chat por API
pip install anthropic
export ANTHROPIC_API_KEY="..."
python scripts/chat_api.py
```

Para cada plataforma (Claude.ai, ChatGPT, Gemini, Copilot Studio, WhatsApp) ver
`docs/guia_migracion_plataformas.md`.

## Principios

- **Corpus cerrado:** solo responde con `knowledge/`.
- **Una sola fuente de reglas:** `prompts/system_prompt.md`.
- **Fidelidad literal:** cifras, plazos y contactos se copian tal cual.
- **Probar antes de publicar:** `evals/casos_prueba.yaml` en cada plataforma.

Prebel S.A. BIC · Reto EstudIA · Versión 1.0 · 2026-11-21
