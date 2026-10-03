---
title: "Manual de usuario"
tags: [paseoya, manual]
status: verificado
updated: 2026-10-03
---

# Manual de usuario

Versión de demostración de PaseoYA para Android (Expo Go), conectada a Supabase. Los datos son ficticios. Todos los recorridos de este manual se ejecutaron contra el backend real el 2026-10-03 (EVID-INT-01a y EVID-INT-02a/b en [[05-Desarrollo/Testing]]), en el emulador y en un teléfono físico.

## Acceso

- **Clientes:** pueden crear su cuenta en «Crear cuenta de cliente», con nombre, correo y contraseña de 8 caracteres o más. Entran directamente a Explorar.
- **Comercios y administración:** no se registran desde la app. Sus cuentas las crea la administración de Paseo Aranjuez (DEC-10).
- **Cuentas de demostración** (contraseña `demo1234`): `cliente@`, `techzone@`, `boutique@` y `admin@paseoya.demo`.
- La sesión se mantiene al cerrar la app. Para salir: Perfil → «Cerrar sesión» (cliente) o «Salir» (comercio y admin).

## Cliente

1. **Explorar:** tiendas por categoría, abiertas o cerradas, y ofertas. Una tienda cerrada muestra su catálogo, pero no deja agregar productos.
2. **Buscar:** escriba un producto; la búsqueda ignora tildes y mayúsculas. Verá las opciones de varios comercios con precio y stock, y puede ordenar por menor precio o mostrar sólo lo que tiene stock.
3. **Agregar:** cada producto va al carrito **de su comercio**. Hay un carrito por tienda y cada uno se paga por separado.
4. **Carritos:**
   - Puede cambiar cantidades, quitar productos o eliminar el carrito.
   - Cada carrito vence **4 horas después de su última modificación**, y en los últimos 5 minutos aparece un aviso.
   - Si el stock cambió, el aviso indica qué corregir antes de pagar («Dejar 6»).
   - Un carrito vencido se puede volver a agregar con los productos que sigan disponibles.
5. **Pagar:**
   - Elija «QR de pago (simulado)» o «Efectivo al retirar» y confirme.
   - Al confirmar se aparta el stock.
   - Si falla la conexión, «Reintentar» no crea un pedido duplicado.
6. **Pedido:**
   - Con QR simulado, pulse «Simular pago»; no se cobra dinero real.
   - Puede **cancelar** sólo mientras el pedido está «Confirmado»; un pago simulado pasa a «Reembolso simulado».
   - Plazos para retirar: 72 horas en efectivo y 14 días con QR. Al vencer, el pedido pasa a «Expirado» automáticamente.
7. **Retiro:**
   - Cuando el comercio marca el pedido como listo, la pantalla se actualiza sola y aparece «Ver código de retiro».
   - El ticket muestra un QR y un PIN de 6 dígitos de un solo uso. «Guardar ticket» lo comparte como imagen.
   - No comparta el código: quien lo presente puede retirar el pedido.
8. **Perfil:** «Reportar un problema», con o sin pedido asociado; lo recibe la administración.

## Comercio

1. **Panel:** muestra sólo los pedidos de su comercio, en las pestañas «Por atender», «Listos» e «Historial». Los pedidos nuevos aparecen solos.
2. Avance cada pedido con «Iniciar preparación» y «Marcar listo para retiro»; el cliente lo ve en su teléfono al instante.
3. **Entrega:**
   - En efectivo, pulse primero «Confirmar pago en efectivo».
   - Escriba el PIN del cliente y pulse «Validar retiro». Un PIN incorrecto, un pedido ajeno o un pago pendiente se rechazan.
   - El PIN sólo sirve una vez.
4. **Ventas entregadas:** total y número de pedidos entregados.

## Administración

Vista de supervisión de sólo lectura: ventas entregadas de la plaza, pedidos por estado, comercios (abiertos o cerrados, con su número de pedidos) y reportes de clientes. La gestión de comercios, categorías, promociones y estadísticas queda fuera de la demo (DEC-19 = A).

## Problemas frecuentes

| Síntoma | Qué hacer |
| --- | --- |
| «Sin conexión con el servidor» | Verificar que el backend esté levantado y pulsar «Reintentar». |
| El botón de herramientas de Expo Go tapa «Perfil» | Arrastrarlo a otro borde de la pantalla. |
| El teléfono no carga la app | Conectar por USB y repetir `adb reverse` (ver README del frontend). |

Fuera de esta versión: recuperación de contraseña, gestión del catálogo desde el comercio, acciones de administración, mapa, avisos y pago bancario real.
