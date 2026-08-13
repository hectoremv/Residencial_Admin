Residencial Admin PWA v6.6

Reconstruida desde v6.4 estable.

Corrección:
- v6.5 perdió roles/modules/menu/buildNav durante una transformación del código. Eso causaba menú muerto y dashboard estático en cero.
- v6.6 valida explícitamente esas definiciones antes de empaquetar.
- Añade error visible si el arranque falla.

Mejoras:
- Movimiento/aporte: residente con autocompletado o persona externa.
- Notificaciones repetidas: compactación y deduplicación por deuda/unidad.
- Reportes: Resumen, Financiero detallado, Cuotas/cobros, Operativo.
- Filtro por fecha, compartir, CSV, PDF.
- Identidad visual configurable: cada organización carga su propio logo desde Administración.
- Logo guardado en IndexedDB/settings y usado en reportes.
- No se incluye ningún logo específico en el código.

Publicación:
Sube todos los archivos y abre repair.html para forzar v6.6. No borres IndexedDB.
