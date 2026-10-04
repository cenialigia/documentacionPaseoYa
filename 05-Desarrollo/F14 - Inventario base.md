---
title: "F14 · Inventario base (F14-00.3)"
tags: [paseoya, f14, inventario]
status: vigente
updated: 2026-10-03
---

# F14 · Inventario base (F14-00.3)

Punto de partida versionado de F14 según [[05-Desarrollo/F14 - Revision y ampliacion por roles|F14-00.3]]: **frontend `cf9c9da`**, **backend `45b0e3e`**, **Core `b0c8625`**. Se registra qué existe con evidencia antes de construir el lote Cliente. «Existe» no significa que cumpla F14: cada fila `SUP` se vuelve a probar al cerrar su tarea. Comercio y Administración se inventarían al abrir sus lotes.

| Tarea F14 | Ruta / archivo actual (frontend) | Backend (tabla · función) | Evidencia previa | Estado frente a F14 |
| --- | --- | --- | --- | --- |
| CLI-01 Splash | `src/app/index.tsx` (carga de sesión) | Supabase Auth | EVID-INT-01a | Parcial: sin splash de marca |
| CLI-02 Bienvenida | — | — | — | No existe |
| CLI-03 Registro | `src/app/(auth)/registro.tsx` | `auth.users` + trigger `crear_perfil_cliente` → `perfiles` | EVID-INT-02a PASS | Parcial: faltan teléfono, género, nacimiento y confirmación de contraseña (DEC-F14-08) |
| CLI-04 Foto | — | sin Storage | — | No existe (DEC-F14-16) |
| CLI-05 Login | `src/app/(auth)/ingresar.tsx` | Auth | EVID-INT-01a PASS | Parcial: sin mostrar contraseña ni recuperación (DEC-F14-09) |
| CLI-06 Inicio | `src/app/(cliente)/(tabs)/explorar.tsx` | `comercios`, `productos` (RLS) | EVID-LUI-03a, EVID-INT-01a | Parcial: barra y secciones distintas (DEC-F14-02) |
| CLI-07 Categoría | filtro dentro de Explorar | `comercios.categoria` (texto) | EVID-LUI-03a | Parcial: sin ruta propia ni tabla (DEC-F14-15) |
| CLI-08 Tienda | `src/app/(cliente)/comercio/[comercioId].tsx` | `productos` | EVID-LUI-03a | Parcial: sin buscador interno ni favoritos |
| CLI-09 Producto | `src/app/(cliente)/producto/[productoId].tsx` | `productos` | EVID-LUI-03a | Parcial: sin promoción ni favoritos |
| CLI-10/16 Carrito | `src/app/(cliente)/(tabs)/carritos.tsx`, `src/state/cart.tsx`, `cart-storage.ts` | — (dispositivo) | EVID-LUI-04a, EVID-CART-a PASS | Existe; pasa al encabezado (DEC-F14-02) |
| CLI-11 Método de pago | `src/app/(cliente)/checkout/[carritoId].tsx` | `confirmar_pedido` | EVID-LUI-05a, EVID-INT-02b PASS | Existe; ajustar copy y precio con promoción |
| CLI-12/13 QR y pago confirmado | QR simulado dentro de `pedido/[pedidoId]/detalle.tsx` | `simular_pago` | EVID-INT-01a PASS | Parcial: sin pantalla propia ni cuenta atrás (DEC-F14-03) |
| CLI-14/15 Tickets | `src/app/(cliente)/pedido/[pedidoId]/ticket.tsx` | `credenciales_retiro` (RLS READY) | EVID-INT-02b PASS | Existe; añadir vista previa antes de READY (DEC-F14-04) |
| CLI-17 Reserva creada | — (navega al detalle) | — | — | No existe |
| CLI-18–22 Pedidos | `src/app/(cliente)/(tabs)/pedidos.tsx`, `detalle.tsx` | `pedidos`, `pedido_lineas` | EVID-INT-01a PASS | Parcial: En curso/Historial → Reservas/Compras/Historial (DEC-F14-10) |
| CLI-23 Promociones | — | — | — | No existe (DEC-F14-11) |
| CLI-24 Favoritos | — | — | — | No existe (DEC-F14-05) |
| CLI-25 Notificaciones | — | — | — | No existe (DEC-F14-05) |
| CLI-26 Perfil | `src/app/(cliente)/cuenta.tsx` | `perfiles`, `reportes` | EVID-DEMO-a, EVID-INT-02a | Parcial: sin foto, datos personales, ayuda/legal ni confirmación de cierre |

**Comunes:** tema `src/constants/theme.ts`; componentes `src/components/ui/*`; datos `src/data/*`; sesión `src/state/auth.tsx`; pedidos `src/state/orders.tsx` (RPC + Realtime). Migraciones: `20261003000000_esquema_demo.sql`, `20261003010000_realtime_y_cron.sql`. Pruebas: `npm run test:db` (17/17), `concurrencia.sh`.
