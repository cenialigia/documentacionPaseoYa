---
title: "F14 · Matriz QA"
tags: [paseoya, f14, qa]
status: vigente
updated: 2026-10-04
---

# F14 · Matriz QA (QA-01 y QA-04)

Trazabilidad de los 54 recortes de [[02-Arquitectura/F14 - Mapa de vistas por rol]] hasta la ruta, el archivo, el contrato de datos, la decisión aplicable, la prueba y la comparación visual. Base: frontend `ec9a897`/`18594b4`, backend `043d0a2`. Rutas de Expo Router (los grupos `(cliente)`, `(comercio)`, `(admin)` no forman parte de la URL). Archivos relativos a `frontend/src/app/`.

**Método de la comparación visual (QA-04):** captura real del emulador Pixel 3a en el mismo estado (pedidos creados por SQL en cada estado y enlaces directos `exp://…/--/ruta`), compuesta lado a lado con el recorte del PDF/mosaico y revisada una por una. Las composiciones quedaron fuera del Core para no cargar el repositorio; se regeneran con el mismo procedimiento. «Coincide» = misma estructura y contenido; las diferencias de color fino, tipografía o fotos de ejemplo no se listan.

**Aceptación:** el usuario probó la demo en su teléfono y revisó el admin sin observaciones (2026-10-04). Los desvíos que derivan de una decisión (DEC) quedan aceptados por esa decisión; los marcados *mejora* son diferencias de diseño sin decisión, aceptadas para la demo y abiertas para una iteración posterior.

## Cliente

| Recorte | Vista | Ruta · archivo | Contrato / datos | DEC | Evidencia | Comparación visual |
| --- | --- | --- | --- | --- | --- | --- |
| CLI-01 | Splash | `/` · `index.tsx` | sesión de Auth | — | EVID-F14-QA-04 | Coincide. Se ve mientras carga la sesión; sin servidor muestra «Sin conexión» (QA-02). |
| CLI-02 | Bienvenida | `/bienvenida` · `(auth)/bienvenida.tsx` | — | DEC-F14-12 | EVID-F14-CLI-a | Sin foto de fondo del mall (fotos de terceros excluidas). |
| CLI-03 | Registro | `/registro` · `(auth)/registro.tsx` | Auth `signUp` + `crear_perfil_cliente` | DEC-F14-08 | EVID-F14-CLI-a | Género con chips en vez de lista desplegable; sin íconos en los campos (*mejora*). |
| CLI-04 | Foto opcional | `/foto-perfil` · `(cliente)/foto-perfil.tsx` | Storage `avatares` (privado) | DEC-F14-16 | EVID-F14-CLI-a/b | Cámara y galería en dos botones; añade «Quitar foto». |
| CLI-05 | Login | `/ingresar` · `(auth)/ingresar.tsx` | Auth contraseña | DEC-F14-09 | EVID-F14-CLI-a | Sin Google/Apple (no decidido); recuperación por código. |
| CLI-06 | Inicio | `/inicio` · `(cliente)/(tabs)/inicio.tsx` | catálogo, `promociones`, `productos_mas_pedidos` | DEC-F14-02 | EVID-F14-CLI-a | Coincide. |
| CLI-07 | Categoría | `/categoria/[categoriaId]` | `comercios` + `categorias` | DEC-F14-15 | EVID-F14-CLI-a | Coincide. |
| CLI-08 | Tienda | `/comercio/[comercioId]` | `productos` activos | — | EVID-F14-CLI-a | Lista a una columna y sin pestañas de subcategoría: el modelo no tiene subcategorías de producto (*mejora*). |
| CLI-09 | Detalle de producto | `/producto/[productoId]` | `precio_vigente` (servidor) | DEC-F14-11, DEC-20 | EVID-F14-BE-a | Sin valoración ★ (DEC-20 retiró reseñas). |
| CLI-10 | Carrito por tienda | `/carritos` · `carritos.tsx` | carrito local por usuario, 4 h | RN-03/04 | EVID-CART-a | Añade «Cómo funciona» y vencimiento; sin miniaturas (*mejora*). |
| CLI-11 | Método de pago | `/checkout/[carritoId]` | `confirmar_pedido` | DEC-04–06 | EVID-F14-CLI-a | Coincide. |
| CLI-12 | QR de pago | `/pago-qr/[pedidoId]` | `simular_pago` | DEC-F14-03 | EVID-F14-CLI-a | Coincide; marca «Simulado · sin valor». |
| CLI-13 | Pago confirmado | `/pago-confirmado/[pedidoId]` | — | DEC-F14-03 | EVID-F14-QA-04 | Coincide. Corregido en QA: encabezado vacío arriba. |
| CLI-14 | Ticket compra QR | `/pedido/[pedidoId]/ticket` | `credenciales_retiro` (sólo dueño, sólo listo) | DEC-16 | EVID-F14-COM-b | Coincide; PIN de respaldo además del QR. |
| CLI-15 | Ticket reserva efectivo | `/pedido/[pedidoId]/ticket` | ídem | DEC-16 | EVID-F14-CLI-a | Coincide. |
| CLI-16 | Carrito restaurante efectivo | `/checkout/[carritoId]` (efectivo) | `confirmar_pedido` | DEC-05 | EVID-F14-CLI-a | El método se elige en el checkout, no en el carrito. |
| CLI-17 | Reserva confirmada | `/reserva-confirmada/[pedidoId]` | — | DEC-06 | EVID-F14-CLI-a | Coincide. Corregido en QA: encabezado vacío. |
| CLI-18 | Mis pedidos | `/pedidos` · `(tabs)/pedidos.tsx` | `pedidos` (RLS) + Realtime | DEC-F14-10 | EVID-F14-CLI-a | Pestañas Compras/Reservas/Historial en vez de Todos/Compras/Reservas (una sola fuente con pestañas). |
| CLI-19 | Detalle de reserva | `/pedido/[pedidoId]/detalle` | `pedidos`, `pedido_lineas` | — | EVID-F14-CLI-a | Coincide; añade línea de estado del pedido. |
| CLI-20 | Mis compras | `/pedidos` (Compras) | ídem | DEC-F14-10 | EVID-F14-CLI-a | Filtro por pestaña en vez de Completadas/En proceso. |
| CLI-21 | Detalle de compra | `/pedido/[pedidoId]/detalle` | ídem | — | EVID-F14-CLI-a | Coincide; añade línea de estado. |
| CLI-22 | Historial | `/pedidos` (Historial) | ídem | DEC-F14-10 | EVID-F14-CLI-a | Lista única con búsqueda en vez de pestañas Compras/Reservas. |
| CLI-23 | Promociones | `/promociones` · `(tabs)/promociones.tsx` | `promociones` aprobadas y vigentes | DEC-F14-11 | EVID-F14-CLI-a | Tarjeta grande en vez de fila compacta (*mejora*). |
| CLI-24 | Favoritos | `/favoritos` | `favoritos` (RLS por dueño) | DEC-F14-05 | EVID-F14-CLI-a | Tarjeta grande en vez de fila compacta (*mejora*). |
| CLI-25 | Notificaciones | `/notificaciones` · `components/lista-avisos.tsx` | `notificaciones` + Realtime | DEC-F14-05 | EVID-F14-CLI-a | Sin avisos de «nueva promoción» al cliente (*mejora*). |
| CLI-26 | Perfil | `/perfil` · `(tabs)/perfil.tsx` | `perfiles`, `eliminar_cuenta` | DEC-F14-05, DEC-24 | EVID-F14-CLI-a | Sin direcciones ni métodos de pago (DEC-F14-05); añade reportar y eliminar cuenta. |

## Comercio

| Recorte | Vista | Ruta · archivo | Contrato / datos | DEC | Evidencia | Comparación visual |
| --- | --- | --- | --- | --- | --- | --- |
| COM-01 | Dashboard | `/panel` · `(comercio)/(tabs)/panel.tsx` | `pedidos`, `comercios.abierto` | DEC-F14-11 | EVID-F14-COM-a | Gráfico de ventas por hora añadido en QA; sin % de crecimiento (métrica no definida). |
| COM-02 | Lista de pedidos | `/ordenes` | `pedidos` (RLS del comercio) | DEC-F14-08 | EVID-F14-COM-a | Sin nombre del cliente en la tarjeta (sólo en el detalle de pedidos activos). |
| COM-03 | Detalle de pedido QR | `/orden/[pedidoId]` | `contacto_cliente`, `avanzar_pedido` | DEC-16, DEC-F14-14 | EVID-F14-COM-a | «Marcar como entregado» lleva a «Gestionar retiro» (no salta la credencial); sin miniaturas. |
| COM-04 | En preparación | `/orden/[pedidoId]` | `avanzar_pedido` | — | EVID-F14-COM-a | Línea de estado añadida en QA. |
| COM-05 | Escáner QR | `/retiro` · `retiro.tsx` | `verificar_retiro` | DEC-F14-13 | EVID-F14-COM-b | Cámara en recuadro, no a pantalla completa; QR leído en teléfono físico. |
| COM-06 | Verificación de retiro | `/retiro` (verificado) | `verificar_retiro` → `confirmar_entrega` | DEC-F14-14 | EVID-F14-COM-a/b | Coincide; sin nombre del cliente. |
| COM-07 | Productos | `/catalogo` · `(tabs)/catalogo.tsx` | `productos` del comercio | — | EVID-F14-COM-a | Coincide. |
| COM-08 | Crear/editar producto | `/editar-producto/[productoId]` | `productos`, Storage `imagenes` | DEC-F14-07 | EVID-F14-COM-a | Sin categoría de producto ni varias fotos (una foto). |
| COM-09 | Detalle de producto | `/producto-comercio/[productoId]` | `productos`, `promociones` | DEC-F14-07 | EVID-F14-COM-a | «Gestionar stock» se hace desde Editar; Eliminar sólo sin pedidos. |
| COM-10 | Ventas | `/ventas` · `(tabs)/ventas.tsx` | `pedidos` pagados | DEC-F14-11 | EVID-F14-COM-a | Gráfico añadido en QA; corregido el monto partido «Bs 150,0 / 0» (bloques a dos columnas). |
| COM-11 | Detalle de venta | `/venta/[pedidoId]` | `pedidos`, `pedido_lineas` | DEC-F14-08 | EVID-F14-COM-a | Sin datos del cliente (pedido cerrado). |
| COM-12 | Editar establecimiento | `/editar-comercio` | `comercios` + `proteger_comercio` | DEC-F14-07 | EVID-F14-COM-a | Nombre, categoría y ubicación de sólo lectura (los fija el admin). |
| COM-13 | Perfil y configuración | `/mi-comercio` | — | DEC-F14-05 | EVID-F14-COM-a | Sin métodos de pago ni preferencias. |
| COM-14 | Notificaciones | `/avisos` | `notificaciones` del comercio | DEC-F14-05, DEC-20 | EVID-F14-COM-a | Sin «stock bajo» ni reseñas. |

## Administrador

| Recorte | Vista | Ruta · archivo | Contrato / datos | DEC | Evidencia | Comparación visual |
| --- | --- | --- | --- | --- | --- | --- |
| ADM-01 | Dashboard | `/admin` · `(admin)/(tabs)/admin.tsx` | `pedidos`, `listar_usuarios`, `promociones` | DEC-F14-11 | EVID-F14-ADM-a | Gráfico de la semana añadido en QA; sin % de crecimiento. |
| ADM-02 | Comercios | `/comercios-admin` | `comercios` (incl. inactivos) | DEC-F14-06 | EVID-F14-ADM-a | Coincide. |
| ADM-03 | Detalle de comercio | `/comercio-admin/[comercioId]` | `comercios`, `cambiar_estado`, estadísticas | DEC-F14-06/07 | EVID-F14-ADM-a | Sin banner, teléfono ni correo del comercio (no están en el modelo). |
| ADM-04 | Usuarios | `/usuarios` | `listar_usuarios` | DEC-F14-06 | EVID-F14-ADM-a | Coincide; sin avatares. |
| ADM-05 | Detalle de usuario | `/usuario/[usuarioId]` | `cambiar_estado_usuario`, `eliminar_cuenta` | DEC-F14-08, DEC-24 | EVID-F14-ADM-a | Sin género ni nacimiento individuales (sólo analítica agregada). |
| ADM-06 | Pedidos | `/pedidos-admin` | `pedidos` (RLS admin) | — | EVID-F14-ADM-a | Coincide. |
| ADM-07 | Detalle de pedido | `/pedido-admin/[pedidoId]` | `pedidos`, `reportes` | DEC-F14-06 | EVID-F14-ADM-a | Sin «Marcar como listo» (el admin no cambia estados); línea de estado añadida. |
| ADM-08 | Productos del comercio | `/comercio-admin/[comercioId]` (Productos) | `productos` + `proteger_producto_admin` | DEC-F14-06 | EVID-F14-ADM-a | Coincide. |
| ADM-09 | Estado de producto | `/producto-admin/[productoId]` | ídem | DEC-F14-06 | EVID-F14-ADM-a | Coincide. |
| ADM-10 | Ventas | `/analitica` (Ventas) | `pedidos` pagados | DEC-F14-11 | EVID-F14-ADM-a | Gráfico por día añadido en QA; sin % de crecimiento. |
| ADM-11 | Analítica | `/analitica` (Resumen/Clientes) | `pedidos`, `listar_usuarios` | DEC-F14-11 | EVID-F14-ADM-a | Barras en vez de línea y dona (*mejora*). |
| ADM-12 | Categorías | `/categorias` · `categoria-form/[categoriaId]` | `categorias` | DEC-F14-15 | EVID-F14-ADM-a | Cuenta comercios, no productos (no hay categoría por producto). |
| ADM-13 | Promociones | `/promociones-admin` · `promocion-form/[promocionId]` | `promociones` + avisos | DEC-F14-11 | EVID-F14-ADM-a | Tarjetas con acciones (aprobar/rechazar/pausar) en vez de interruptores. |
| ADM-14 | Perfil admin | `/perfil-admin` | — | DEC-F14-05 | EVID-F14-ADM-a | Sin preferencias ni notificaciones configurables (no decididas). |

## Resumen

- 54/54 recortes con ruta, archivo, contrato y evidencia; ninguna vista del PDF quedó sin implementar.
- 18 coinciden; 29 difieren por una decisión documentada (DEC), por el modelo de datos o porque agregan funciones; 7 son *mejoras* de diseño sin decisión, aceptadas para la demo.
- Defectos encontrados y corregidos por la comparación: encabezado vacío en las confirmaciones, monto partido en Ventas, falta de gráfico de ventas (4 vistas) y de línea de estado del pedido (3 vistas).
