---
title: "F14 · Mapa de vistas por rol"
tags: [paseoya, ui, mockup]
status: propuesto
updated: 2026-10-03
---

# F14 · Mapa de vistas por rol

**54 recortes navegables:** 26 Cliente, 14 Comercio y 14 Administrador. Se preservan también los PDF y mosaicos completos en [[09-Entradas/_Indice de entradas]]. Los recortes incluyen el número/título visible cuando el mosaico lo ofrece; en Cliente algunas columnas son estrechas y se conservan pequeños márgenes vecinos para no cortar controles. Son referencias visuales, no evidencia de UI implementada.

| Rol | Mapa de capturas, rutas y tareas | Navegación principal propuesta por PDF | Evidencia previa que exige supervisión |
| --- | --- | --- | --- |
| Cliente | [[02-Arquitectura/F14 - Cliente - vistas y tareas]] | Inicio · Mis pedidos · Promociones · Perfil; corazón/campana/carrito en header, **pendiente DEC-F14-02/05** | LUI-03–06, INT-01/02, EVID-CART-a; LUI-07 parcial |
| Comercio | [[02-Arquitectura/F14 - Comercio - vistas y tareas]] | Inicio · Pedidos · Productos · Ventas; avatar→Perfil | LUI-08, BE-01/03/04, INT-02 |
| Administrador | [[02-Arquitectura/F14 - Administrador - vistas y tareas]] | Inicio · Comercios · Usuarios · Pedidos · Más; avatar→Perfil, **captura discrepa** | LUI-09 lectura parcial, EVID-DEMO-a/INT-01a |

**Estados transversales:** carga, contenido, vacío, búsqueda sin resultados, error, éxito, offline, sesión vencida, cambios sin guardar y confirmaciones contextuales. No crear una pantalla principal por cada estado ni duplicar el módulo de una pestaña con otra lista intermedia. QR de pago simulado y credencial de retiro son objetos visual y funcionalmente distintos. RLS, stock, estado de pago y estado de pedido se verifican en backend y dispositivo, no sólo por la captura.

**Relación de fuentes:** SRC-04 Stitch sigue siendo la dirección visual aprobada en DEC-11. SRC-08–13 proponen ampliaciones por rol; toda divergencia con decisiones anteriores aparece en [[02-Arquitectura/Decisiones F14 antes de iniciar]].
