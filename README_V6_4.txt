RESIDENCIAL ADMIN PWA v6.4 — RECOVERY

CAUSA REAL ENCONTRADA
El JavaScript tenía una cadena rota en la función Compartir informe:
.join('\n') terminó guardada físicamente en dos líneas dentro de una cadena con comillas simples.
Eso produce SyntaxError y hace que TODO el JavaScript deje de ejecutarse:
- menú no responde
- dashboard queda en 0
- IndexedDB no se lee
- Portal y botones no funcionan

CORREGIDO
- Sintaxis JS reparada y validada con Node.
- repair.html para eliminar únicamente Service Worker/Cache Storage.
- IndexedDB NO se toca.
- v6.4 visible en encabezado.
- navegación network-first.
- actualización del Service Worker sin cache.

PASOS
1. Subir TODOS los archivos.
2. Esperar GitHub Pages.
3. Abrir /repair.html en la misma ruta del proyecto.
4. Pulsar Abrir Residencial Admin v6.4.
5. Confirmar v6.4 en encabezado y menú funcional.
