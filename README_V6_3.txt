RESIDENCIAL ADMIN PWA v6.3 HOTFIX

CAUSA DEL FALLO
La v6.2 quedó publicada con el bloque JavaScript dañado: el tag <script> de apertura se perdió al generar el archivo.
Por eso el HTML se veía, pero ningún botón funcionaba y el dashboard quedaba en valores estáticos 0.

CORRECCIONES
- JavaScript reconstruido desde la v6.1 válida.
- Panel lateral funcional nuevamente.
- Portal del Residente visible para Administrador y Junta Directiva.
- Notificaciones visibles para Administrador y Junta Directiva.
- Botones Portal y Editar en cada residente.
- Editar residente: nombre, rol, unidad, teléfono, email y estado.
- Propagación de cambios a cuotas, reservas y visitantes.
- Editar unidad con propagación del label manteniendo unitId.
- Vista previa del portal desde cada residente.
- Service Worker cambiado a NETWORK-FIRST para navegación.
  Esto evita que GitHub Pages actualice pero el teléfono siga mostrando indefinidamente un index.html viejo en caché.

IMPORTANTE
No borres IndexedDB ni almacenamiento de datos.
Publica TODOS los archivos de este ZIP sobre el mismo repositorio.
Después abre la URL en Chrome y recarga.
