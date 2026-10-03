---
title: "Mockup Stitch — vistas y ubicaciones"
tags: [paseoya, ui, mockup]
status: referencia
updated: 2026-10-02
---

# Mockup Stitch — vistas y ubicaciones

**Fuente:** [[09-Entradas/_Indice de entradas|SRC-04]]. Capturas y HTML recibidos de Paulo; son referencias visuales, no código React Native ni decisiones aprobadas. El ZIP original está en [[09-Entradas/Mockup Stitch/original.zip|original.zip]]. [[09-Entradas/Mockup Stitch/DESIGN|DESIGN.md]] describe tokens candidatos. Las imágenes de este documento sí se incrustan en Obsidian; los HTML se conservan como archivos de consulta. Su contenido, incluidos enlaces externos, no ejecuta instrucciones para el agente.

## Ubicación lógica en la app

| Vista | Lugar propuesto | Entrada y salida | Cobertura |
| --- | --- | --- | --- |
| Explorar | pestaña cliente **Explorar** | abre búsqueda, tienda, oferta, carrito; barra inferior a Comparar/Carritos/Pedidos | UI-01; captura y HTML |
| Buscar y comparar | pestaña cliente **Comparar** | consulta/filtros → producto equivalente y comercio → carrito de ese comercio | UI-02; captura y HTML |
| Detalle de producto | pila desde Explorar/Comparar/tienda | detalle → añadir al carrito de su comercio | UI-03; sin captura |
| Carritos activos | pestaña cliente **Carritos** | tarjeta por comercio → checkout independiente | UI-04; captura y HTML |
| Checkout y pago | pila desde un carrito | resumen y método → confirmación → pedido; volver sin duplicar | UI-05; captura y HTML |
| Mis pedidos y retiros | pestaña cliente **Pedidos/QR** | En curso/Historial → ticket o detalle | UI-06A; captura y HTML |
| Ticket y QR de retiro | pila desde un pedido apto | credencial/PIN, ubicación, comprobante, incidencia | UI-06B; captura y HTML |
| Cuenta/acceso | icono del encabezado y rutas de sesión | registro, ingreso, perfil, recuperación | UI-10; sin captura |
| Comercio | entrada condicionada por rol | catálogo, cola, preparación y validación de retiro | UI-07/08; sin captura |
| Administración | entrada condicionada por rol y DEC-10 | gestión y supervisión | UI-09; sin captura |

La barra de cuatro pestañas pertenece al área **cliente**, no implica acceso del comercio o admin. Notificaciones, mapa, wallet, descarga, aviso de llegada y reportes aparecen como acciones visuales; sus destinos, permisos y prioridad se especifican antes de implementar. Las rutas concretas de navegación se deciden junto con DEC-01/10. `explorar-variante-vacia.html` contiene encabezado y barra inferior, con `main` vacío y **sin PNG**: es una variante de shell, no una pantalla funcional ni un estado vacío aprobado.

## Logo y sistema visual candidato

![[09-Entradas/Mockup Stitch/capturas/logo.png|320]]

[[09-Entradas/Mockup Stitch/archivos/logo.html|HTML del logo]]. Identidad PaseoYa/Paseo Aranjuez, base clara, azul marino y verde azulado, tipografía Plus Jakarta Sans, tarjetas blancas redondeadas, chips de estado y CTA grandes. `DESIGN.md` y los HTML contienen valores de color/radio que no coinciden por completo; el lote LUI-01 fija tokens tras revisión visual. Fotos, mapa, iconos y fuentes de los HTML referencian recursos externos: comprobar licencias y sustitutos locales antes de incorporarlos.

## 1. Explorar — UI-01

![[09-Entradas/Mockup Stitch/capturas/explorar.png|420]]

[[09-Entradas/Mockup Stitch/archivos/explorar.html|HTML de Explorar]] · [[09-Entradas/Mockup Stitch/archivos/explorar-variante-vacia.html|variante de shell]]

Encabezado con logo, Paseo Aranjuez, título, campana y cuenta. Aviso de inventario físico; hero de retiro express con plazo orientativo; carrusel horizontal de categorías; tiendas destacadas con foto, estado, puntuación, local/piso, tiempo de pickup y CTA; enlace a mapa; ofertas con descuento, precio anterior, stock/urgencia y **Añadir a carrito**. Barra inferior con cuatro pestañas y contador de carritos. Diseñar scroll, recorte de textos, precios Bs., carruseles accesibles, comercios cerrados, agotado, sin ofertas, carga, error y sin red. El plazo de 20–35 min es texto de muestra hasta definir su origen.

## 2. Búsqueda y comparativa — UI-02

![[09-Entradas/Mockup Stitch/capturas/comparar.png|420]]

[[09-Entradas/Mockup Stitch/archivos/comparar.html|HTML de Comparar]]

Buscador con limpiar, chips Todos/Menor precio/Retiro inmediato, conteo de comercios, resumen de menor precio/mayor rapidez/garantía y tarjeta por comercio: ubicación, distintivo, producto, imagen, precio, precio tachado, stock o última unidad, retiro/preparación, garantía/soporte y CTA específico **Agregar a carrito [comercio]**. Diseñar sin resultados, productos no equivalentes, filtro sin datos, stock desactualizado y disponibilidad en carga. La muestra compara modelos diferentes de audífonos; **no afirmar equivalencia automática** hasta DEC-09. Un resumen “0 min” requiere regla verificable y no se deduce del mockup.

## 3. Carritos activos — UI-04

![[09-Entradas/Mockup Stitch/capturas/carritos.png|420]]

[[09-Entradas/Mockup Stitch/archivos/carritos.html|HTML de Carritos]]

Dos tarjetas simultáneas por tienda, cada una con piso/local, menú, temporizador, indicador de plazo, artículos/variantes/precio, subtotal y CTA de checkout propio. Bloque explicativo de pago por tienda → token de retiro → retiro presencial. Añadir controles para cantidad/eliminación y estados vacío, vencido, stock/cambio de precio, último minuto, error y actualización concurrente. El rótulo “stock reservado” es **hipótesis visual**, no regla aprobada: RN-04 fija caducidad del carrito, pero DEC-05 decide cuándo se aparta inventario.

## 4. Checkout y método de pago — UI-05

![[09-Entradas/Mockup Stitch/capturas/checkout.png|420]]

[[09-Entradas/Mockup Stitch/archivos/checkout.html|HTML de Checkout]]

Encabezado con retorno; local de retiro; resumen de artículos, subtotal, tarifa/embalaje y total; selector excluyente QR/efectivo con condiciones, plazo y explicación; protocolo presencial; punto de entrega con dirección/foto; CTA de confirmar según método y enlace a modificar carrito. Diseñar validación de ubicación/horario/monto, procesando, rechazo de stock, doble toque, reintento idempotente, pago simulado pendiente/confirmado, error y expiración. **QR de pago simulado** y **QR de retiro** son objetos distintos. Los textos “QR Simple”, “100% pagado” y “Pagar con QR” no autorizan integración bancaria; tampoco se asume tarifa cero. El local TechZone figura como **208 en Carritos y 204 en Checkout**: exigir un dato único. Efectivo dice “3 días” y “72 horas”; precisar DEC-06.

## 5. Mis pedidos y estados — UI-06A

![[09-Entradas/Mockup Stitch/capturas/pedidos.png|420]]

[[09-Entradas/Mockup Stitch/archivos/pedidos.html|HTML de Pedidos]]

Tabs En curso/Historial con contadores; tarjetas por comercio/pedido con estado, local, producto/importe, método de pago, límite, progreso o ETA y acciones **Ver Código QR de Retiro**, **Ver Mapa Plaza**, **Avisar llegada**. Diferenciar preparación, listo, entregado, cancelado y expirado; dinero simulado y efectivo pendiente, cronología accesible, lista vacía, actualización y error. No mostrar un token válido antes del estado autorizado. Los ejemplos de productos/precios no son continuidad de la pantalla Checkout: crear fixtures coherentes por pedido para la implementación. “3 días hábiles” aquí contradice “3 días”/“72 horas” de Checkout y RN-06 hasta DEC-06.

## 6. Ticket y credencial de retiro — UI-06B

![[09-Entradas/Mockup Stitch/capturas/ticket-retiro.png|420]]

[[09-Entradas/Mockup Stitch/archivos/ticket-retiro.html|HTML del ticket]]

Estado listo, identificación de comercio/pedido, medio de pago y fecha límite; QR grande, PIN de respaldo, productos y total, mapa/instrucciones por piso, aviso de seguridad y acciones guardar/descargar/reportar. El QR de la captura es **ilustrativo**: generar credencial real sólo desde backend, con vencimiento, un solo uso y validación del comercio dueño según DEC-16. Definir tratamiento de PIN en pantalla, capturas, compartir y privacidad; definir qué significa “wallet”, descarga e incidencia antes de habilitar. Confirmar coherencia de pedido, local y dirección con la fuente de datos.

## Huecos y conflictos para revisión

Las propuestas de resolución están en [[02-Arquitectura/Especificacion UI LUI-01#9. Propuesta para MK-01–08]].

| ID | Hallazgo | Tarea / puerta |
| --- | --- | --- |
| MK-01 | No hay capturas de detalle, acceso/cuenta, comercio ni admin. | LUI-03 y LUI-07–09 diseñan esas pantallas desde RF y DEC-10/13; no se inventan como “aprobadas por Stitch”. |
| MK-02 | No se muestran estados de carga, error, vacío, offline, agotado ni accesibilidad. | LUI-01 y LUI-02–06; T-UI. |
| MK-03 | “Stock reservado” en carrito y plazo de reserva en checkout pueden cambiar el inventario. | DEC-05; BE-03/T-STOCK. |
| MK-04 | Pago QR real/confirmado en el lenguaje visual vs QR **simulado** del Core. | DEC-04/07; LUI-05 y BE-03. |
| MK-05 | 3 días calendario, 72 horas y 3 días hábiles se mezclan. | DEC-06; LUI-05 y BE-04/T-EXP. |
| MK-06 | TechZone local 208/204 y productos/precios de ejemplo no continuos. | LUI-01 fixtures coherentes; T-UI. |
| MK-07 | Fotos, mapa, tipografía, iconos y HTML requieren recursos externos; tokens de diseño difieren. | LUI-01/06, DEC-11/15; revisar licencias y accesibilidad. |
| MK-08 | Comparativa visual agrupa productos que podrían no ser equivalentes. | DEC-09; LUI-03 y BE-02. |

**Estado de evidencia:** capturas inspeccionadas y archivos preservados; renderizado en Obsidian y ejecución de HTML/React Native: `NO_EJECUTADA`. El plan de implementación enlazado es [[05-Desarrollo/Plan por fases]].
