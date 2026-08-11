RESIDENCIAL ADMIN PWA v5

NUEVO NIVEL
- Usuarios y roles locales por departamento:
  Administrador, Tesorero, Seguridad, Mantenimiento, Junta Directiva y Consulta.
- Menú dinámico según el rol activo.
- Ficha completa por unidad.
- Estado de cuenta por unidad.
- Cuotas mensuales por unidad.
- Mora / recargo configurable y aplicación mensual.
- Registro de pagos que distribuye el monto a cuotas pendientes.
- Movimientos financieros asociados a unidades.
- Órdenes de trabajo avanzadas:
  categoría, prioridad, responsable, proveedor, costo estimado, costo real y estado.
- Control de visitantes:
  unidad, autorizado por, motivo, vehículo/placa, hora de entrada y salida.
- Auditoría con usuario.
- Respaldo versionado.
- Compatibilidad de importación con Tesorería v3+ y Residencial Admin v4/v5.

NOTA DE SEGURIDAD
Los roles de esta PWA son controles funcionales locales, no autenticación fuerte multiusuario.
La seguridad real por usuario requiere backend/servidor y será la siguiente etapa cuando decidamos sincronizar en la nube.

RECOMENDACIÓN DE PUBLICACIÓN
Usa el mismo repositorio nuevo que creaste para Residencial Admin.
Reemplaza los archivos v4 por los de v5. No borres datos del navegador.
IndexedDB sube automáticamente de versión 1 a 2 y crea la tabla users.

PRÓXIMO NIVEL
- Portal del residente
- Archivos/fotos de comprobantes y mantenimiento
- Notificaciones y vencimientos
- Presupuesto anual y cuentas por pagar
- Control de acceso QR
- Sincronización cloud y autenticación real
