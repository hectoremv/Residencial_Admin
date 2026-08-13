# Residencial Admin — PWA

**Versión actual:** 7.2  
**Estado:** PWA local/offline en evolución hacia una plataforma con backend central, app móvil Android (APK) y portal web de escritorio.

## 1. Propósito

Residencial Admin es un sistema administrativo genérico para:

- Condominios.
- Residenciales.
- Juntas de vecinos.
- Asociaciones comunitarias.

La aplicación no está ligada a una organización específica. Cada instalación puede configurar su nombre, tipo, datos institucionales y logo.

## 2. Arquitectura actual

La versión actual es una PWA que funciona principalmente en el dispositivo:

- HTML/CSS/JavaScript.
- IndexedDB para almacenamiento local.
- Service Worker con navegación network-first.
- Manifest PWA para instalación.
- Respaldo/restauración en JSON.
- Funcionamiento offline después de cargar los recursos.

Los registros nuevos utilizan IDs estables y campos de auditoría (`createdAt`, `updatedAt`, `createdBy`, `updatedBy`, `syncStatus`) para facilitar la futura migración a una API y base de datos central.

> Los perfiles/roles actuales son controles funcionales locales; todavía no constituyen autenticación multiusuario fuerte.

## 3. Módulos

### Inicio / Dashboard
- Balance disponible.
- Unidades.
- Residentes activos.
- Cuentas por cobrar.
- Órdenes de mantenimiento abiertas.
- Ingresos y gastos del mes.
- Alertas sin leer.
- Estado general de los datos.
- Acciones rápidas.
- Actividad reciente con descripciones amigables.

### Residentes y unidades
- Registro de residentes.
- Búsqueda por nombre, teléfono o unidad.
- Edición de residente.
- Detección preventiva de nombres duplicados.
- Propietario, inquilino, familiar u otro.
- Estado activo/inactivo.
- Asociación opcional a unidad.
- Edición de unidades.
- Ficha de unidad con estado de cuenta, residentes, mantenimiento y accesos.
- Vista previa del Portal del Residente.

### Tesorería
- Ingresos.
- Gastos.
- Aportes patrocinados/directos.
- Persona vinculada a residente o persona externa.
- Búsqueda automática de residentes.
- Asociación por `residentId` y `unitId`.
- Anulación de movimientos conservando el historial.
- Balance calculado excluyendo movimientos anulados.

### Cuotas y cobros
La base de cobranza es configurable:

- **Residente / miembro:** recomendado para juntas de vecinos y asociaciones.
- **Unidad / propiedad:** recomendado para condominios y residenciales.

Incluye:
- Generación mensual de cuotas.
- Días de gracia.
- Mora/recargo porcentual.
- Registro de pagos.
- Aplicación del pago a cuotas pendientes en orden cronológico.
- Estado pagado/parcial/pendiente/anulado.
- Previsualización antes de generar cuotas: período, base de cobro, registros, duplicados, monto unitario y total.
- Selección múltiple de cuotas.
- Anulación con motivo, usuario y fecha, sin afectar cuentas por cobrar.
- Eliminación definitiva restringida a Administrador y solo para cuotas sin pagos, abonos ni recargos.
- Los pagos nuevos guardan su distribución por cuota para fortalecer la trazabilidad y futura reversión.
- Compatibilidad con cuotas históricas basadas en miembro.

### Mantenimiento
- Órdenes de trabajo.
- Unidad o área común.
- Categoría.
- Prioridad.
- Responsable.
- Proveedor.
- Costo estimado y real.
- Estados de seguimiento.

### Seguridad y accesos
- Visitantes.
- Unidad.
- Persona que autoriza.
- Motivo.
- Vehículo/placa.
- Hora de entrada y salida.
- Incidentes y severidad.
- Autorizaciones desde el Portal del Residente.

### Áreas comunes
- Reservas.
- Fecha y horario.
- Residente.
- Estado de la reserva.

### Comunicaciones
- Avisos.
- Circulares.
- Audiencia.
- Publicaciones visibles para residentes.

### Reuniones y actas
- Reuniones de directiva.
- Asambleas ordinarias y extraordinarias.
- Comités.
- Estado.
- Acuerdos.

### Documentos
- Reglamentos.
- Actas.
- Contratos.
- Referencias.
- Actividades históricas migradas desde versiones anteriores.

### Activos e inventario
- Bienes y equipos.
- Categoría.
- Cantidad.
- Ubicación.
- Condición.

### Proveedores
- Empresa/persona.
- Servicio.
- Teléfono.
- Correo.

### Portal del Residente
- Vista personal por residente.
- Estado de cuenta.
- Balance pendiente.
- Pagos del año.
- Reservas activas.
- Solicitudes de mantenimiento.
- Notificaciones.
- Registrar pago.
- Reservar área.
- Solicitar mantenimiento.
- Autorizar visitante.

En el futuro, con autenticación real, el residente accederá directamente a su propia cuenta sin seleccionar manualmente su perfil.

### Notificaciones
- Cuotas pendientes.
- Seguimiento de mantenimiento.
- Leído/no leído.
- Deduplicación por deuda/unidad.
- Compactación automática de duplicados históricos.

### Informes
Tipos disponibles:
- Resumen administrativo.
- Financiero detallado.
- Cuotas y cobros.
- Operativo.

Funciones:
- Filtro por fechas.
- Compartir usando la función nativa del celular (incluido WhatsApp).
- CSV.
- PDF/Imprimir.
- Encabezado institucional con logo a la izquierda y títulos centrados, similar al encabezado principal de la app.
- Logo y datos institucionales.

### Administración
- Organización.
- Tipo.
- Administrador/tesorero.
- Base de cobranza.
- Cuota.
- Mora.
- Días de gracia.
- Identificación/RNC.
- Teléfono.
- Correo.
- Dirección.
- Eslogan.
- Logo.
- Usuarios/roles.
- Salud de datos.
- Respaldo.
- Restauración.
- Auditoría.

## 4. Roles

- Administrador.
- Tesorero.
- Seguridad.
- Mantenimiento.
- Junta Directiva.
- Consulta.
- Residente.

Los módulos visibles dependen del perfil activo.

## 5. Identidad visual

Cada organización puede cargar su propio logo desde:

**Administración → Identidad visual → Cargar logo**

El logo se guarda actualmente en la configuración local (IndexedDB) y se utiliza en los informes.

No se incorpora ningún logo específico en el código fuente.

Para la futura plataforma:
- El logo se almacenará en el backend/cloud.
- La organización tendrá tema/colores institucionales.
- Logo y datos oficiales podrán aparecer en recibos, facturas, estados de cuenta, reportes, circulares y PDFs.

## 6. Salud de datos

Administración incluye una revisión rápida de:
- Posibles residentes duplicados.
- Residentes sin teléfono/correo.
- Cuotas con relaciones huérfanas.
- Antigüedad del último respaldo.

El Dashboard muestra avisos cuando existe algo importante que revisar.

## 7. Respaldo y restauración

### Exportar
**Administración → Exportar respaldo**

Genera un JSON con:
- Versión de aplicación.
- Versión de esquema.
- Configuración.
- Usuarios.
- Unidades.
- Residentes.
- Movimientos.
- Cuotas.
- Mantenimiento.
- Seguridad.
- Reservas.
- Comunicaciones.
- Reuniones.
- Documentos.
- Activos.
- Proveedores.
- Notificaciones.
- Auditoría.

### Restaurar
**Administración → Restaurar**

También conserva compatibilidad con respaldos históricos de Tesorería compatibles.

### Recomendación
Realizar un respaldo:
- Después de una jornada con muchos cambios.
- Antes de actualizar la aplicación.
- Como mínimo una vez por semana.

## 8. Actualización en GitHub Pages

1. Hacer un respaldo.
2. Reemplazar los archivos del repositorio por la versión nueva.
3. Hacer Commit.
4. Esperar a que GitHub Pages publique.
5. Si el teléfono conserva una versión vieja, abrir `repair.html`.
6. Pulsar el botón para limpiar únicamente Service Worker/Cache Storage.
7. Abrir la aplicación actualizada.

`repair.html` **no elimina IndexedDB**.

No usar “Borrar datos del sitio” salvo que exista un respaldo y se quiera reiniciar completamente la instalación.

## 9. Instalación PWA

Desde el navegador compatible:
- Abrir la URL publicada.
- Usar el botón **Instalar** cuando aparezca.
- También puede utilizarse “Añadir a pantalla de inicio”.

## 10. Modelo de datos y compatibilidad futura

Principios:
- IDs estables.
- Relaciones por IDs, no únicamente por nombres.
- Auditoría.
- Timestamps.
- Estados en vez de eliminación destructiva cuando corresponde.
- `syncStatus` preparado para sincronización futura.

Esto permitirá reutilizar la lógica al construir:
1. Backend/API central.
2. Base de datos SQL/cloud.
3. Aplicación Android APK.
4. Web administrativa de escritorio.
5. Portal web/app del residente.

## 11. Limitaciones actuales

- Los datos están principalmente en el dispositivo.
- No existe sincronización real entre varios teléfonos.
- Los roles no tienen contraseña/autenticación fuerte.
- Los adjuntos/documentos todavía no se almacenan como archivos en nube.
- No existen notificaciones push del servidor.
- No hay procesamiento de pagos bancarios en línea.

## 12. Hoja de ruta

Próximas fases previstas:
- Backend/API.
- Autenticación real y permisos.
- Multi-organización.
- Sincronización.
- Portal independiente del residente.
- APK Android.
- Web de escritorio.
- Adjuntos/fotos/comprobantes.
- Presupuesto anual.
- Cuentas por pagar/compras.
- Recibos y comprobantes formales.
- Notificaciones push.
- QR/control de acceso.
- Integraciones de pago.
- Dashboard analítico avanzado.

## 13. Historial resumido

El proyecto evolucionó desde una aplicación de Tesorería hacia Residencial Admin:

- Tesorería PWA: aportes, gastos, reportes y respaldos.
- v4: estructura administrativa modular.
- v5: roles, fichas de unidad, cuotas, mora y órdenes de trabajo.
- v6: Portal del Residente, notificaciones, IDs relacionales y preparación para sincronización.
- v6.4: recuperación y estrategia de caché robusta.
- v6.6: identidad visual configurable, reportes diversificados, autocompletado de residentes y deduplicación de notificaciones.
- **v7.0:** auditoría integral, salud de datos, dashboard ejecutivo, cobranza adaptable por residente/unidad, anulación segura de movimientos, configuración institucional ampliada y documentación consolidada.
- **v7.1:** encabezado institucional de reportes rediseñado con logo lateral, tipo de organización y nombre centrados.
- **v7.2:** gestión segura de cuotas: previsualización de generación, selección múltiple, anulación auditada, eliminación administrativa protegida y trazabilidad de aplicación de pagos.

## 14. Seguridad operativa

Antes de cualquier actualización importante:
1. Exportar respaldo.
2. Confirmar que el archivo JSON fue descargado.
3. Actualizar.
4. Verificar Dashboard, Residentes, Tesorería e Informes.

Nunca depender de una sola copia de los datos locales.
