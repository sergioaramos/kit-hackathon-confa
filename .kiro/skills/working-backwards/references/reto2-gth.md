# Reto 2: autogestión de solicitudes de GTH (resumen de la guía oficial)

**Reto:** autogestión centralizada, simple para el colaborador y muy flexible por dentro, para trámites de Talento Humano: vacaciones, incapacidades, certificados, permisos no remunerados.

## Usuarios
- Colaboradores que radican solicitudes.
- Aprobadores: líder directo y otras áreas según el caso.
- Equipo de GTH, que configura trámites y rutas.

## Requisitos funcionales (Ajuste al reto: 15 pts)
- Radicación intuitiva con adjuntos (soportes de incapacidad).
- **Crear trámites nuevos sin programar.**
- Rutas de aprobación según el caso: solo líder, varias personas o escalamiento.
- Bandeja independiente por aprobador.
- Correo en cada cambio de estado.
- Trazabilidad completa visible para el colaborador.

## Recursos del evento
- Plataforma de RR. HH.: **por confirmar → mock** con contrato claro (no penaliza).
- RDS del evento para solicitudes.
- Servicios mencionados en la capacitación: AWS Step Functions (ejecutar la ruta), Amazon SES (correos).

## Métricas sugeridas
Tiempo total del ciclo · % con trazabilidad completa · solicitudes perdidas o reprocesadas · horas de GTH ahorradas al mes · tiempo para configurar un trámite nuevo.

## Ángulos con evidencia (ver evidencia-y-supuestos.md)
- ~1.200 colaboradores × ~5 trámites al año ≈ 500 solicitudes al mes [supuesto].
- ~42 h al mes de GTH respondiendo "¿en qué va lo mío?" [supuesto: 5 min por consulta].
- Incapacidades: el empleador paga los días 1-2 y recobra a la EPS desde el día 3; un soporte incompleto demora el recobro [verificar].
- Los participantes de la hackathon son colaboradores: encuesta a mano alzada en el kickoff.

## Desafíos
- Rutas configurables sin reprogramar.
- Datos de salud: el aprobador no ve diagnósticos.
