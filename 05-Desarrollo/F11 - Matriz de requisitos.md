---
title: "F11 · Matriz de requisitos"
tags: [paseoya, f11, qa]
status: vigente
updated: 2026-10-04
---

# F11 · Matriz de requisitos (COMP-04)

Cada requisito de [[09-Entradas/requisitosPaseoYa]] (RF-01–44, RN-01–09, §11–14 y RNF-01–10) → implementación → evidencia. Base: frontend `main`, backend `main` (incluye `20261008000000_f11_trazabilidad.sql`). Las vistas por rol están en [[05-Desarrollo/F14 - Matriz QA]]; las evidencias en [[05-Desarrollo/Testing]].

**Estados:** PASS = implementado y probado · PARCIAL = cubierto con límite declarado · DECISIÓN = depende de una respuesta de Usuario.

## Requisitos funcionales

| RF | Requisito | Implementación | Evidencia | Estado |
| --- | --- | --- | --- | --- |
| RF-01 | Registro | `(auth)/registro.tsx`, Auth `signUp` + `crear_perfil_cliente` (rol CLIENTE fijo) | EVID-F14-CLI-a, EVID-INT-02a | PASS |
| RF-02 | Inicio de sesión | `(auth)/ingresar.tsx`, Auth por contraseña | EVID-INT-01a, EVID-F14-CLI-a | PASS |
| RF-03 | Gestión de sesión | sesión guardada (`expo-sqlite`), renovación del token, «Sin conexión» sin cerrar sesión, vuelta a la bienvenida si vence | EVID-CART-a, EVID-F14-QA-02 | PASS |
| RF-04 | Perfil | datos personales, foto (subir/quitar), eliminar cuenta | EVID-F14-CLI-a/b, EVID-DEC24-a | PASS |
| RF-05 | Listar comercios | Inicio y Categoría | EVID-F14-CLI-a | PASS |
| RF-06 | Consultar comercio | `comercio/[comercioId]`: ubicación, horario, estado, descripción | EVID-F14-CLI-a | PASS |
| RF-07 | Listar productos | productos activos por comercio (RLS) | EVID-F14-CLI-a | PASS |
| RF-08 | Categorías | tabla `categorias`, `categoria/[categoriaId]` | EVID-F14-CLI-a, EVID-F14-ADM-a | PASS |
| RF-09 | Búsqueda global | `buscar.tsx` en todo el marketplace, sin distinguir tildes | EVID-F14-CLI-a | PASS |
| RF-10 | Comparación | la búsqueda muestra el producto en cada tienda con precio y stock, filtros «Menor precio» y «Con stock» | EVID-F14-CLI-a | PARCIAL: compara por nombre; sin catálogo de equivalencias (DEC-09) |
| RF-11 | Detalle de producto | `producto/[productoId]` con precio vigente y descripción | EVID-F14-CLI-a | PASS |
| RF-12 | Disponibilidad | etiquetas «N disponibles», «Última unidad», «Agotado»; el servidor rechaza sin stock | EVID-F14-CLI-a, EVID-BE-b | PASS |
| RF-13 | Crear carrito | carrito por comercio al agregar | EVID-CART-a | PASS |
| RF-14 | Múltiples carritos | uno por comercio, por usuario | EVID-CART-a | PASS |
| RF-15 | Consultar carritos | `carritos.tsx` con vencimiento visible | EVID-CART-a | PASS |
| RF-16 | Modificar carrito | agregar, quitar, cantidades | EVID-F14-CLI-a | PASS |
| RF-17 | Expirar carrito (4 h) | vence a las 4 h desde el último cambio y pasa a «Vencidos» | EVID-CART-a | PARCIAL: el carrito vive en el dispositivo (RN-05); no se sincroniza entre equipos |
| RF-18 | Crear pedido | `confirmar_pedido`: un comercio, stock atómico, idempotente | EVID-INT-01a, EVID-BE-a/b | PASS |
| RF-19 | Método de pago | QR simulado o efectivo en el checkout | EVID-F14-CLI-a | PASS |
| RF-20 | Pago QR simulado | `simular_pago`, QR que vence en 5 min | EVID-F14-CLI-a, EVID-DEMO-NUBE-a | PASS |
| RF-21 | Reserva en efectivo | pedido EFECTIVO con plazo de 72 h | EVID-F14-CLI-a, EVID-DEMO-NUBE-a | PASS |
| RF-22 | Código de retiro único | `credenciales_retiro` (PIN) + QR con el id del pedido | EVID-F14-COM-b, EVID-F14-QA-03 | PASS: el QR es único; un PIN suelto ambiguo se rechaza |
| RF-23 | Consultar pedido | detalle y ticket: productos, comercio, total, método, estado, fechas y código | EVID-F14-CLI-a | PASS |
| RF-24 | Historial | Mis pedidos → Historial con búsqueda | EVID-F14-CLI-a | PASS |
| RF-25 | Cancelación | `cancelar_pedido` sólo en CONFIRMED; QR pagado → REFUNDED; stock devuelto | EVID-F14-CLI-a, pruebas T-CAN | PASS |
| RF-26 | Expiración | `expirar_pedidos` con pg_cron cada minuto | EVID-INT-02a, EVID-BE-d | PASS |
| RF-27 | Crear producto | comercio, con foto y descripción | EVID-LUI-08a, EVID-F14-COM-a | PASS |
| RF-28 | Editar producto | formulario con aviso de cambios sin guardar | EVID-F14-COM-a | PASS |
| RF-29 | Modificar precio | edición validada en cliente y servidor | EVID-LUI-08a | PASS |
| RF-30 | Gestionar stock | edición con control de concurrencia optimista | EVID-LUI-08a | PASS |
| RF-31 | Activar/desactivar | comercio y admin, con confirmación | EVID-F14-COM-a, EVID-F14-ADM-a | PASS |
| RF-32 | Consultar pedidos | `ordenes` por estado, pago y búsqueda (RLS del comercio) | EVID-F14-COM-a | PASS |
| RF-33 | Confirmar pedido | el pedido nace CONFIRMED al pagar o reservar (stock ya apartado); el comercio lo acepta con «Empezar preparación» o lo **rechaza con motivo** (`rechazar_pedido`: cancela, reembolsa el QR simulado, devuelve stock y avisa al cliente) | EVID-F11-a | PASS (DEC-F11-01) |
| RF-34 | Preparar pedido | `avanzar_pedido` → IN_PREPARATION | EVID-F14-COM-a | PASS |
| RF-35 | Marcar listo | `avanzar_pedido` → READY_FOR_PICKUP | EVID-F14-COM-a | PASS |
| RF-36 | Validar retiro | `verificar_retiro` (QR o PIN, sin consumir) + `confirmar_entrega` | EVID-F14-COM-a/b | PASS |
| RF-37 | Pago en efectivo | `confirmar_efectivo` antes de entregar | EVID-F14-COM-a, EVID-DEMO-NUBE-a | PASS |
| RF-38 | Consultar ventas | pestaña Ventas por periodo, gráfico y detalle | EVID-F14-COM-a | PASS |
| RF-39 | Gestionar usuarios | listar, activar/desactivar, eliminar datos de cliente | EVID-F14-ADM-a, EVID-DEC24-a | PASS |
| RF-40 | Gestionar comercios | alta con cuenta, edición, abrir/cerrar, activar/desactivar | EVID-F14-ADM-a | PASS |
| RF-41 | Gestionar categorías | crear, editar, desactivar, borrar sin comercios | EVID-F14-ADM-a | PASS |
| RF-42 | Supervisar pedidos | pedidos de toda la plaza con historial completo | EVID-F14-ADM-a, EVID-F11-a | PASS |
| RF-43 | Estadísticas | Inicio y Analítica con definiciones (venta = pagado) | EVID-F14-ADM-a | PASS |
| RF-44 | Promociones | aprobar, rechazar, pausar, crear (sólo %) | EVID-F14-ADM-a, EVID-F14-BE-c | PASS |

## Reglas de negocio

| Regla | Implementación | Evidencia | Estado |
| --- | --- | --- | --- |
| RN-01 Retiro presencial | sin delivery; entrega sólo con código en el local | EVID-F14-COM-b | PASS |
| RN-02 Un pedido, un comercio | `confirmar_pedido` rechaza productos de otro comercio | pruebas T-CHECKOUT | PASS |
| RN-03 Múltiples carritos | uno por comercio | EVID-CART-a | PASS |
| RN-04 Expiración del carrito | 4 h desde el último cambio | EVID-CART-a | PASS |
| RN-05 Carrito ≠ pedido | carrito local; pedido en el servidor | EVID-CART-a, EVID-INT-01a | PASS |
| RN-06 Reserva en efectivo 72 h | `vence_en` + `expirar_pedidos` | EVID-INT-02a | PASS |
| RN-07 Pedido QR 14 días | vencido y pagado → RETAINED (DEC-07) | pruebas T-EXP | PASS |
| RN-08 Reembolso por cancelación | QR pagado y cancelado → REFUNDED, stock devuelto | pruebas T-CAN | PASS |
| RN-09 Concurrencia | bloqueo de filas en una transacción | EVID-BE-b | PASS |
| §11 Stock disponible y reservado | el stock publicado es el disponible; lo apartado vuelve al vencer o cancelar; el comercio ve las unidades reservadas en pedidos en curso | EVID-F11-a | PASS |
| §12 Estados del pedido | enum PostgreSQL; el pedido nace CONFIRMED porque la confirmación del pago o la reserva aparta el stock (DEC-F11-01); el estado CREATED de la propuesta no se usa | pruebas SQL | PASS |
| §13 Estados del pago | PENDING, PAID, REFUNDED, RETAINED, separados del estado del pedido | pruebas SQL | PASS |
| §14 Código de retiro | PIN visible sólo al dueño en «listo»; un solo uso | EVID-F14-QA-03 | PASS |

## Requisitos no funcionales

| RNF | Implementación | Evidencia | Estado |
| --- | --- | --- | --- |
| RNF-01 Seguridad | Supabase Auth; clave pública en la app, sin claves secretas | EVID-BE-c, EVID-F14-QA-03 | PASS |
| RNF-02 Control de acceso | rol en `perfiles`; funciones que validan el rol; rutas por rol en la app | EVID-F14-QA-02/03 | PASS |
| RNF-03 RLS | políticas por tabla y por rol | EVID-F14-QA-03 (39/39) | PASS |
| RNF-04 Integridad del inventario | stock atómico | EVID-BE-b | PASS |
| RNF-05 Consistencia | pedido, pago, inventario y reserva en funciones transaccionales | pruebas SQL | PASS |
| RNF-06 Trazabilidad | `pedido_eventos`: cada estado y pago con fecha y autor (o «Sistema»); visible según el pedido; historial en el admin | EVID-F11-a | PASS |
| RNF-07 Disponibilidad | nube Supabase; «Sin conexión» con reintento | EVID-DEMO-NUBE-a, EVID-F14-QA-02 | PASS para la demo; monitoreo pendiente (F12) |
| RNF-08 Escalabilidad | comercios y productos se agregan sin cambiar el esquema (Bold y Librería Central creados en uso) | EVID-F14-ADM-a | PASS |
| RNF-09 Usabilidad | compra en cinco pasos; auditoría de accesibilidad | EVID-F14-QA-02 | PARCIAL: TalkBack y texto al 200 % pendientes |
| RNF-10 Mantenibilidad | código modular por rol, datos y estado; migraciones versionadas; lint y tipos | revisión de código | PASS |

## Resultado

- **RF:** 42 PASS, 2 PARCIAL (RF-10, RF-17).
- **RN y §11–14:** 13/13 PASS (§11 y RNF-06 cerrados en F11).
- **RNF:** 9 PASS, 1 PARCIAL (RNF-09).
- **Huecos que quedan:** equivalencias de productos para comparar (DEC-09); carrito sincronizado entre equipos (opcional); TalkBack y texto al 200 %; paginación de búsquedas cuando el catálogo crezca.
