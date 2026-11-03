# Kit Agentic Mindset Hackathon · CONFA × AWS

Kit de trabajo para construir, en día y medio, una solución con agentes de IA (Strands + Amazon Bedrock AgentCore) usando Kiro con desarrollo guiado por specs. Sirve para los dos retos: eventos y solicitudes de GTH.

No contiene datos internos de CONFA: solo metodología, información pública y referencias técnicas.

## Usarlo en 3 pasos

1. **Copia** las carpetas `.kiro/` y `docs/` y los archivos `AGENTS.md` y `evidencia-y-supuestos.md` a la raíz del repositorio del equipo.
2. **Llena** `.kiro/steering/producto.md` cuando elijan el reto (o deja que lo llene `/working-backwards`).
3. **Sigue el flujo** en el chat de Kiro (o de Claude Code):

```
/working-backwards  →  /spec-requisitos  →  /spec-diseno  →  /spec-tareas  →  /implementar (una tarea por vez)
                                                                                     ↓ al cerrar cada bloque
                                                                               /auditoria
                                                                                     ↓ jueves temprano
                                                                               /presentacion
```

## Qué trae

| Pieza | Qué hace |
|---|---|
| `skills/working-backwards` | Las 5 preguntas del cliente y el comunicado de prensa → `docs/working-backwards.md` |
| `skills/spec-requisitos` | Comunicado → `.kiro/specs/<slug>/requirements.md` en notación EARS, con contingencias |
| `skills/spec-diseno` | Requisitos → `design.md`: patrón de agentes, modelos de Bedrock justificados, AgentCore, seguridad |
| `skills/spec-tareas` | Diseño → `tasks.md` con TDD embebido y un primer recorrido de punta a punta |
| `skills/implementar` | Implementa **una** tarea: prueba en rojo → código → verde → marca la tarea |
| `skills/agentcore-strands` | **Referencia técnica verificada** (CLI `@aws/agentcore` 1.0.1, Strands 1.63). Se activa sola al escribir código de agentes |
| `skills/auditoria` | 6 lentes de auditoría: seguridad, strands, agentcore, codigo, tests, spec-rubrica |
| `skills/presentacion` | Presentación HTML animada de un solo archivo (con cronómetro y notas) + guion + preguntas del jurado |
| `steering/` | Contexto permanente: producto, tecnología y seguridad (Ley 1581) |
| `agents/auditor.json` | Auditor para Kiro CLI (`kiro-cli chat --agent auditor`) |
| `hooks/` | Revisión de secretos al guardar archivos Python |

## Auditorías: cuándo correr cada lente

| Momento | Lentes |
|---|---|
| Al cerrar un bloque de tareas | `codigo` + `tests` + `strands` (+ `seguridad` si tocó datos) |
| Antes de `agentcore deploy` | `agentcore` + `seguridad` |
| Jueves antes de presentar | `spec-rubrica` |

En Kiro, si el agente custom no está disponible: abre un **chat nuevo** (contexto limpio) y escribe `/auditoria seguridad`.

## Pendiente de validar en Kiro el día del evento
- Formato del hook (`.kiro/hooks/`) y del agente custom (`.kiro/agents/`): escritos según la documentación de Kiro, no probados.
- Si Kiro muestra las specs en su panel cuando las crea una skill (deberían estar en `.kiro/specs/<slug>/`).

## En Claude Code
`.claude/skills` es un enlace a `.kiro/skills` (una sola copia). Los auditores están en `.claude/agents/` como subagentes de solo lectura.
