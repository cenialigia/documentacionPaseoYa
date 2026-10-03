---
title: "Definición del proyecto"
tags: [paseoya]
status: planificado
updated: 2026-10-02
---

# Definición del proyecto

## Identidad y problema

PaseoYA es una aplicación móvil para los establecimientos del Paseo Aranjuez. Permite descubrir comercios, productos, precios y disponibilidad; reservar/comprar anticipadamente y **retirar físicamente en el comercio correspondiente**. El objetivo del reto es digitalizar ventas y atraer visitas presenciales. Fuente: [[09-Entradas/_Indice de entradas|SRC-01, PDF del reto, §§5.2–5.6]].

## Usuarios

| Actor | Necesidad principal | Fuentes |
| --- | --- | --- |
| Cliente | Buscar/comparar, formar carrito por comercio, pedir y presentar código de retiro | PDF §5.7; MD §§4, 15, 18–21 |
| Comercio | Publicar productos, stock y precios; preparar y entregar pedidos | PDF §5.7; MD §§4, 16, 22–23 |
| Administración del Paseo | Gestionar comercios/usuarios/categorías; supervisar pedidos y estadísticas | PDF §5.7; MD §§4, 24 |

## Alcance solicitado para el MVP

Marketplace multi-comercio, autenticación por rol, categorías, búsqueda/comparación, múltiples carritos separados por comercio, checkout QR **simulado** o efectivo, pedido con código/QR de retiro, flujo del comercio, validación presencial, inventario consistente y vencimientos automáticos. El MD añade reglas 4 horas, 3 días y 14 días que requieren definición operativa y prueba. Detalle en [[04-Reglas-de-negocio/_Indice de reglas]].

## Alcance diferido

Delivery, integración bancaria real, sistemas comerciales reales, Paseo Points, Jarvis y funciones de IA no son el núcleo del MVP. Favoritos, cupones y otras mejoras figuran como adicionales en el PDF y futuras en el MD. Promociones/estadísticas sí aparecen como capacidades administrativas del reto, pero su profundidad en la demo está por priorizar.

## Criterio de éxito para el hackathon

Una persona demuestra en vivo: cliente localiza producto, crea pedido de **un** comercio, el comercio lo confirma y prepara, el cliente presenta código y el comercio marca entrega. También se muestran al menos el segundo método de pago simulado/reserva, protección de stock, roles y comportamiento de vencimiento mediante reloj de prueba o evidencia reproducible. El entregable oficial incluye prototipo funcional, código fuente, presentación, demo y explicación de arquitectura (PDF §§7–9). Alcance exacto de demo pendiente en [[02-Arquitectura/Decisiones pendientes]].

**Estado real:** carpeta de proyecto inicialmente vacía. No hay app, base, cuentas ni pruebas ejecutadas. React Native + Supabase/PostgreSQL es la tecnología indicada por Usuario, no una obligación del PDF.

