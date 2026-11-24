# La Cava — Demo de gestión

Demo web (un solo `index.html`, sin backend) de un sistema de gestión para restaurante.
Sitio: https://haperez86.github.io/La-cava/

## Perfiles

- **Mesero** (pensado para celular): abre la mesa escaneando su QR, le asigna pedidos y recibe un aviso cuando Preparación marca el pedido como listo. No puede abrir mesas sin el QR.
- **Preparación**: recibe las comandas; *Iniciar preparación* → *Listo · avisar al mesero*.
- **Cajero**: cobra la cuenta de la mesa (caja abierta obligatoria), imprime y reimprime la factura (formato tirilla de 80 mm), arqueo y cierre.
- **Administrador**: todo lo anterior más menú, inventario, informes y usuarios.

## Funcionalidades principales

- Estados de la mesa visibles: Disponible / Ocupada y, si está ocupada, el estado de su pedido (Pendiente, En preparación, **Listo para recoger**, Servido).
- Inventario por producto con lotes, **fecha de vencimiento** y **temporada**. Lo vendido se descuenta primero del lote que vence antes. Un producto agotado, vencido o fuera de temporada deja de ofrecerse en la carta.
- Filtros en Pedidos, Menú e Inventario.
- Informe mensual con **productos más vendidos** y exportación a Excel.

## Cómo probar la demo

- Usa el selector de perfil de la barra superior. Con el perfil Mesero aparece además el selector del mesero.
- Para escanear una mesa sin QR físico, escribe el código `LACAVA:MESA:1` a `LACAVA:MESA:12` (o `M4`).
- Para ver los avisos en vivo, abre dos pestañas del mismo navegador: una en **Preparación** y otra en **Mesero**. Al marcar un pedido como listo, el mesero recibe el aviso.
- Los datos se guardan en el navegador (`localStorage`). Para volver a los datos de ejemplo, usa **Restablecer datos de demo** en el menú lateral.

## Limitaciones (requieren backend)

- Los avisos solo funcionan entre pestañas del mismo navegador. Para avisar entre dispositivos distintos (cocina → celular del mesero) se necesita un servidor (WebSocket o notificaciones push).
- La lectura del QR con cámara usa `BarcodeDetector` (Chrome/Android). En Safari de iPhone se escribe el código manualmente.
- La factura es un comprobante de demostración: no es factura electrónica DIAN (sin CUFE).
- Los perfiles se simulan; no hay autenticación real.

## Publicación

Se despliega a GitHub Pages con GitHub Actions (`.github/workflows/deploy-pages.yml`) en cada push a `main`.
