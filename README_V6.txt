RESIDENCIAL ADMIN PWA v6

FASE ACTUAL
PWA local/offline, diseñada como base funcional para futura plataforma con:
- Backend/API central
- APK Android
- Web de escritorio

NUEVO EN v6
1. Portal del Residente
   - Selección de residente
   - Unidad asociada
   - Balance pendiente
   - Pagado en el año
   - Estado de cuenta
   - Notificaciones
   - Reservas
   - Solicitudes de mantenimiento
   - Autorización previa de visitantes

2. Notificaciones
   - Cuotas pendientes
   - Seguimiento de mantenimiento
   - Centro de notificaciones
   - Leído/no leído
   - Dedupe para no repetir alertas

3. Arquitectura preparada para backend
   - schemaVersion 3
   - createdAt / updatedAt
   - createdBy / updatedBy
   - syncStatus
   - unitId / residentId
   - backfill automático de registros antiguos
   - relaciones por ID cuando es posible

4. Estado de cuenta por unidad/residente
   - Cargos de cuotas y mora
   - Créditos por pagos
   - Balance pendiente

5. Roles
   - Agrega rol Residente
   - Portal disponible como módulo separado

6. Compatibilidad
   - IndexedDB sube de versión y conserva datos existentes.
   - Backfill automático completa IDs y timestamps faltantes.
   - Respaldo pasa a version 6 / schemaVersion 3.

IMPORTANTE
Esta PWA sigue siendo local. Los roles no son autenticación fuerte.
Cuando migremos a backend, los modelos y relaciones creados aquí servirán directamente como base para SQL/API.
