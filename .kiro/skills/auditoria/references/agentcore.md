# Lente: agentcore (infraestructura y despliegue) — Arquitectura agéntica, 15 pts

## Antes de `agentcore deploy`
- [ ] `agentcore/agentcore.json` declara solo lo que usa el diseño: Runtime + Memory y/o Gateway, cada uno con su razón en `design.md`.
- [ ] `agentcore/aws-targets.json` apunta a la **cuenta y región correctas** (desarrollo: cuenta del proveedor; despliegue final: cuenta de CONFA, según el kickoff).
- [ ] `agentcore dev` + `agentcore invoke --runtime <n> --local` funcionan antes de desplegar.
- [ ] Dependencias en `app/<agente>/pyproject.toml` (agregadas con `uv add`), incluidas las que usa el código; no hay imports de paquetes no declarados.
- [ ] `model/load.py` usa un ID de modelo **habilitado en la cuenta** y con perfil de inferencia (`us.`/`global.`); el modo `LOCAL_MODEL=ollama` no queda activo en el despliegue.
- [ ] Nada de credenciales en `agentcore.json`, `pyproject.toml` ni en el código. Las API keys van en `agentcore add credentials` (AgentCore Identity).

## Memory
- [ ] `eventExpiryDuration` justificado (3-365 días).
- [ ] Estrategias necesarias y no todas por defecto (la plantilla trae SEMANTIC, USER_PREFERENCE, SUMMARIZATION y EPISODIC: quitar las que no se usen).
- [ ] `actorId` real del usuario en el payload (no `"default"`), para que la memoria no se mezcle entre personas.
- [ ] No se guardan datos sensibles en la memoria (diagnósticos, imágenes).

## Gateway
- [ ] Autorizador definido (`AWS_IAM` o `CUSTOM_JWT`); `NONE` solo con justificación.
- [ ] Targets con contrato (OpenAPI) y nombres de herramientas claros.
- [ ] La URL y el token del gateway llegan al agente por variable de entorno o Identity, no escritos en el código.

## Observabilidad y demo
- [ ] `agentcore traces` y `agentcore logs` muestran la ejecución (para enseñar en la demo cómo razonó el agente).
- [ ] Hay un plan B si el despliegue falla: correr con `agentcore dev` en local, más un video corto de respaldo.
- [ ] Se probó el endpoint desplegado con `agentcore invoke --runtime <n> --payload ...` y la sesión se mantiene con `--session-id`.
