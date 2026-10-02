---
title: "Plan de pruebas y evidencia"
tags: [paseoya]
status: planificado
updated: 2026-10-02
---

# Plan de pruebas y evidencia

Pruebas diseñadas, **ninguna ejecutada**. Fuentes: PDF §§5–9 y MD RF-01–44/RN-01–09. Datos ficticios; separar cuentas cliente, comercio A, comercio B y admin.

| ID | Caso y resultado esperado | Requisito/fase |
| --- | --- | --- |
| T-F0 | `node`/gestor/toolchain/Supabase CLI observados con versiones; dos raíces Git independientes; arranque y migración local si aplica. | F0, DEC-01/02 |
| T-CAT | Búsqueda/categoría muestra comercio, precio, stock y ubicación; agotado claro. | RF-05–12, UI F3/BE F7 |
| T-RLS | Cliente no lee otro pedido; comercio A no lee/escribe B; usuario normal no administra; intento directo API rechazado. | RNF-01–03, BE F7/F9 |
| T-CART | Dos carritos por comercio; editar cantidades; caduca uno tras 4 h sin alterar pedido ya creado. | RN-02–05, RF-13–17, UI F4/BE F8 |
| T-ORD | Checkout crea un pedido de un comercio; snapshot de precio y estados de pago/pedido separados. | RN-02/05, RF-18–23, BE F8 |
| T-CHECKOUT | QR simulado y efectivo siguen rutas diferentes; error/reintento no duplica pedido ni cobra. | RF-19–22, UI F4/BE F8 |
| T-STOCK | Dos compras concurrentes con una unidad: una se acepta, otra se rechaza; stock nunca negativo, sin doble liberación. | RN-09, RNF-04/05, BE F8 |
| T-CAN | Cancelación antes de preparación, reembolso simulado y stock revertido una vez; tarde se rechaza. | RN-08, RF-25, BE F9 |
| T-RET | Código inválido/ajeno/usado/expirado se rechaza; comercio dueño valida una vez y marca entregado. | RN-01, RF-22/36/37, BE F9 |
| T-EXP | Reloj controlado o simulación de tiempo demuestra 4 h, 3 d y 14 d según DEC-06; proceso funciona sin app abierta y se puede reejecutar sin doble efecto. | RN-04/06/07, RF-17/26, BE F9 |
| T-UI | Navegación móvil con lector de pantalla/tamaños táctiles, errores/offline/vacíos; comparar capturas con diseño aprobado y verificar ubicaciones/acciones UI-01–06B y UI-07–10. | RNF-07/09, UI F1–F6 |
| T-DEMO | Recorrido end-to-end en dispositivo/entorno anunciado; presentación, código y arquitectura disponibles. | PDF §9, F10 |
| T-FULL | Matriz RF-01–44/RN/RNF con prueba y evidencia por cada RF; CRUD comercio, ventas, admin, estadísticas, promociones y extras aprobados sin rutas muertas. | F11, DEC-12/13/20–22 |
| T-OPS | Build/distribución del destino, control de acceso, carga, accesibilidad, respaldo/restauración, migración/reversa, alerta e incidente ensayados. | F12, DEC-23/24 |
| T-PIL | UAT cliente/comercio/admin con datos autorizados, monitoreo del periodo acordado y aceptación o decisión de detener. | F13, DEC-25 |

Registrar `EVID-ID | fecha | versión | dispositivo/ambiente | datos sintéticos | pasos/comando | observado | PASS/FAIL/NO_EJECUTADA | límite`. Un esquema SQL que compila no prueba RLS ni la demo. Si falta entorno, escribir NO_EJECUTADA con motivo. No usar datos reales sin permiso.
