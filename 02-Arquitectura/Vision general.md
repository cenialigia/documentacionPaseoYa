---
title: "Visión general de arquitectura"
tags: [paseoya]
status: planificado
updated: 2026-10-02
---

# Visión general de arquitectura

## Sistema propuesto

```text
React Native (cliente, comercio, admin por definir)
  ├─ exploración y formularios
  ├─ sesión/autorización de UI
  └─ SDK/API de Supabase (identidad del usuario)
          ↓
Supabase Auth + PostgreSQL con RLS + Storage opcional
          ├─ lectura de catálogos según políticas
          ├─ mutaciones simples autorizadas
          └─ operación confiable de checkout, reserva,
             transición y retiro (diseño por decidir)
          ↓
trabajo programado: vencimientos y reparación de estados
(mecanismo por decidir; nunca depende de app abierta)
```

No hay backend NestJS ni frontend Next.js en el alcance tecnológico declarado. Versiones SDK/servicios no seleccionadas.

## Modelo relacional candidato, no schema aprobado

`profiles`, `merchants`, `merchant_memberships`, `categories`, `products`, `stock`, `carts`, `cart_items`, `orders`, `order_items`, `payment_events`, `pickup_credentials`, `order_events`. Imágenes mediante almacenamiento con política explícita. Productos de servicio, promociones y estadísticas requieren decisión antes de tablas adicionales.

Invariantes: pedido y carrito de un solo comercio; snapshots de nombre/precio del producto al confirmar; estados de pedido y pago separados; transición y cambio de stock atómicos; un comercio sólo ve sus pedidos; cliente sólo sus pedidos; administrador según rol; código de retiro validado por el comercio dueño y de un solo uso. La app no decide por sí sola si hay stock ni se atribuye rol admin.

## Flujos

1. Descubrir: comercios/categorías → búsqueda global → detalle/comparación.
2. Comprar: carrito por comercio → checkout → método QR simulado o efectivo → operación consistente de pedido/reserva → código de retiro.
3. Preparar: comercio confirma → prepara → listo para retirar.
4. Retirar: cliente presenta credencial → comercio verifica → registra pago en efectivo si aplica → entrega.
5. Expirar/cancelar: proceso confiable evalúa plazo y estado → libera o liquida stock una vez → deja evento auditable.

El orden y las transiciones concretas están en [[04-Reglas-de-negocio/_Indice de reglas]]. El modelo es una hipótesis para planificar, no DDL ni garantía de seguridad.

