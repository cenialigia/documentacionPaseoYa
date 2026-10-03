---
title: "Decisiones del propietario antes de F14"
tags: [paseoya, decisiones, fase14]
status: pendiente
updated: 2026-10-03
---

# Decisiones del propietario antes de F14

**Uso:** al abrir F14, el agente relee código y este Core, genera la lista actualizada de dudas y pregunta a Paulo **antes de implementar cada lote afectado**. Registrar respuesta literal, fecha, alcance y cambios a RF/RN/DEC/ADR, UI, backend y pruebas. Los tres PDF son propuestas anexas y no sustituyen decisiones previas. Ninguna pregunta de esta tabla está respondida por las imágenes. [[05-Desarrollo/F14 - Revision y ampliacion por roles|F14-00]].

| ID | Decisión que debe tomar Paulo | Motivo y bloqueo |
| --- | --- | --- |
| **DEC-F14-01** | ¿Las nuevas vistas son objetivo de la demo A, cobertura B o una versión posterior? ¿Fecha, orden por rol y aceptación de F14? | DEC-19 fijó demo A; los PDF piden experiencia ampliada. Define prioridad y denominador, no reabre F11–13 automáticamente. |
| **DEC-F14-02** | Cliente: ¿cuál será la barra final? Actual `Explorar/Buscar/Carritos/Pedidos`; PDF `Inicio/Mis pedidos/Promociones/Perfil`; mosaico `Inicio/Pedidos/QR/Favoritos/Perfil`. ¿Carrito en header? ¿La pestaña QR tiene destino propio? | Los tres esquemas son incompatibles. Bloquea shell, rutas y pruebas de navegación. También decidir menú admin: PDF `Inicio/Comercios/Usuarios/Pedidos/Más` frente a captura con `Productos` como quinta pestaña. |
| **DEC-F14-03** | ¿Mantener pago QR **simulado** con botón «Simular pago» según DEC-04 o iniciar un proyecto separado de cobro real? Para simulación: ¿habrá pantalla QR de pago y qué significa su expiración visual? | CLI-12 se parece a QR bancario y muestra 04:58; PDF habla de confirmar pago. El modelo actual no mueve dinero. Pago real exige proveedor, titularidad, conciliación y nuevos permisos, fuera de lo decidido. |
| **DEC-F14-04** | ¿Mantener la credencial de retiro oculta hasta `READY_FOR_PICKUP` (DEC-16) o cambiar esa regla? ¿Qué muestran los tickets de reserva/compra antes de estar listos? | CLI-14/15 y PDF parecen generar QR de recojo inmediatamente; el backend actual sólo habilita QR+PIN de un uso cuando está listo. Afecta seguridad y flujo de cliente/comercio. |
| **DEC-F14-05** | ¿Se reactivan notificaciones/campana, favoritos, promociones, reseñas/descuentos y las opciones nuevas de perfil (direcciones, métodos de pago)? Para cada una: fuente, responsable, persistencia, eventos y prioridad. | DEC-20 retiró campana y valoración/descuentos; DEC-13/22 siguen pendientes. CLI-23–26 y COM-14 no se activan por aparecer en mockup. |
| **DEC-F14-06** | ¿Qué operaciones exactas puede hacer admin? En particular: activar/desactivar producto de un comercio, editar comercio, crear/editar categoría/promoción, modificar usuario y cambiar un pedido a listo. | El PDF admin permite visibilidad de producto pero veta edición de precio/stock y dice que el detalle de pedido es de supervisión; ADM-07 de la imagen ofrece «Marcar como listo». Definir rol, auditoría y RLS. |
| **DEC-F14-07** | ¿Qué campos de comercio mantiene el comerciante y cuáles admin? ¿Puede eliminar un producto con pedidos históricos, o sólo desactivarlo? ¿Quién define horario, categoría, piso/local, foto y métodos de pago? | DEC-21 abierto; COM-09 muestra «Eliminar» y COM-12 editar local. Requiere política de integridad, permisos y publicación. |
| **DEC-F14-08** | ¿El registro exigirá teléfono, género y fecha de nacimiento? ¿Con qué finalidad, obligatoriedad, validación, visibilidad admin, retención y edición? ¿Se permite foto de perfil/cámara/galería? | El PDF cliente los hace obligatorios; el registro actual sólo tiene evidencia básica. Implica datos personales, RLS y Storage, además de DEC-24. |
| **DEC-F14-09** | ¿Google/Apple serán proveedores de login reales o se retirarán de CLI-05? ¿Se requiere recuperación de contraseña y verificación de correo? | La imagen enseña Google/Apple; LUI-07 sigue abierto por recuperación. El PDF descarta verificación de correo en registro; política Auth y cuentas debe ser explícita. |
| **DEC-F14-10** | ¿Cómo se clasifican y muestran pedidos `PENDING`, QR confirmado, reserva, compra, entregado, cancelado y expirado? ¿Una fuente con filtros o listas distintas? ¿Qué aparece en Historial? | PDF cliente: historial sólo entregados; CLI-22 muestra otras etiquetas. Debe concordar con BE-03/04, DEC-07 y pago separado. |
| **DEC-F14-11** | ¿Qué modelo y métrica sustentan promociones, descuentos, 2x1, ventas, ticket promedio, crecimiento, recomendaciones y «más pedidos»? ¿Qué periodo/zona y qué cuenta como venta? | Admin/cliente/comercio muestran números, gráficos y ofertas sin definición. Evitar que se calculen con pagos pendientes o seed ficticio como si fueran datos reales. |
| **DEC-F14-12** | ¿Se mantiene TechZone en Local 208 · Planta baja, trato formal y paleta/tokens aprobados en DEC-11? ¿Cuáles fotos/logos de los nuevos mosaicos tienen licencia para usar? | Capturas muestran TechStore/TechZone en otros locales, personas y marcas, además de tuteo. Son referencia visual, no datos aprobados. Resolver antes de incorporar assets o copy. |
| **DEC-F14-13** | ¿El escáner de comercio usará cámara real en Android/iOS y PIN manual de respaldo? ¿Cuáles dispositivos y permisos se aceptan para la fase? | COM-05/06 del mosaico y PDF piden cámara; hoy sólo hay evidencia de PIN. Autorizar librería compatible, manejo de permisos y prueba física; no instalar SDK por inferencia. |
| **DEC-F14-14** | Tras validar QR/PIN, ¿el pedido se entrega en la misma operación atómica actual o habrá una segunda confirmación humana dentro de COM-05? ¿Cómo se evita consumir la credencial sin entrega? | El PDF y COM-06 muestran Verificación → Confirmar entrega; el backend probado usa validación de PIN de un uso que ya deja `DELIVERED`. Cambiarlo afecta RPC, estado y recuperación ante fallos. |

## Orden mínimo de preguntas al iniciar

1. Preguntar primero **DEC-F14-01–04** y **06**: cambian alcance, rutas, pago, seguridad y permisos.
2. Preguntar **05, 07–14** antes de los lotes que las necesitan. Se puede supervisar pantallas existentes mientras tanto.
3. Para cualquier dato nuevo descubierto al leer el código, añadir `DEC-F14-15+` con alternativa, efecto y responsable, y preguntarlo antes de implementar. Si Paulo conserva DEC-04/11/16/20, la imagen se adapta a esas decisiones y la divergencia se documenta.

**Registro de respuesta:** `ID | pregunta | respuesta de Paulo | fecha | ámbito | artefactos afectados | prueba | estado`. Hasta recibirla, todas estas filas permanecen **PENDIENTE**; no hay aceptación tácita del contenido de los PDF. Los formularios históricos viven en [[02-Arquitectura/Decisiones de Usuario para el desarrollo]].
