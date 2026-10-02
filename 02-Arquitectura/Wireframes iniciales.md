---
title: "Wireframes iniciales — propuesta V0"
tags: [paseoya]
status: planificado
updated: 2026-10-02
---

# Wireframes iniciales — propuesta V0

Bocetos de baja fidelidad para discutir jerarquía y recorridos. No son capturas, renders ni decisión final de marca. Ancho móvil ilustrativo.

## UI-01 Descubrir

```text
┌──────────────────────────────┐
│ PaseoYA             Cuenta ○ │
│ ¿Qué buscas hoy? [Buscar…]   │
│ Categorías   Ver todas       │
│ [Tecnología] [Comida] [Moda] │
│ Comercios cercanos           │
│ [Foto] Tienda A · abierto    │
│ [Foto] Tienda B · horario    │
│ Inicio  Buscar  Carritos  Yo │
└──────────────────────────────┘
```

## UI-02 Comparar y UI-03 producto

```text
┌──────────────────────────────┐
│ ← Audífonos                 ⌕ │
│ [imagen / alternativa]       │
│ Orden: precio | disponibilidad│
│ Tienda A  Bs 250  disponible │
│ Tienda B  Bs 260  agotado    │
│ Ver ubicación / horario      │
│ [Detalle] [Agregar a carrito]│
└──────────────────────────────┘
```

Comparación debe identificar variantes reales y no presentar productos diferentes como idénticos sin criterio (DEC-09).

## UI-04 Carritos y UI-05 checkout

```text
┌──────────────────────────────┐
│ Carritos (2)                 │
│ [Tienda A] vence en 03:10    │
│  Audífonos    − 1 +  Bs 250  │
│  Total: Bs 250               │
│  [Continuar con Tienda A]    │
│ [Tienda B] vence en 02:30    │
│  Mouse        − 1 +   Bs 80  │
│  [Continuar con Tienda B]    │
└──────────────────────────────┘
┌──────────────────────────────┐
│ Checkout · Tienda A          │
│ Retiro: ubicación + horario  │
│ Resumen: 1 artículo  Bs 250  │
│ ( ) QR simulado  ( ) Efectivo│
│ Fecha límite: según método  │
│ [Confirmar pedido]           │
│ error/espera: no duplicar    │
└──────────────────────────────┘
```

## UI-06 Pedido y UI-08 comercio

```text
┌──────────────────────────────┐
│ Pedido #PY-...               │
│ Listo para recoger           │
│ Tienda A · ubicación/horario │
│ Retirar antes de: fecha/hora │
│ [QR DE RETIRO]  PIN respaldo │
│ Pago: simulado / pendiente   │
│ [Ver detalle]                │
└──────────────────────────────┘
┌──────────────────────────────┐
│ Comercio · Pedidos           │
│ [Nuevos] [Preparando] [Listos]│
│ #PY-... · efectivo           │
│ [Confirmar] [Preparar]       │
│ [Marcar listo]               │
│ Retiro: [Escanear] [PIN]     │
│ [Validar y entregar]         │
└──────────────────────────────┘
```

**Puntos de revisión:** contrastes/lectura, tamaño táctil, ubicación visible, diferencia entre QR de pago y QR de retiro, múltiples carritos claros, estados de error y accesibilidad. No generar imágenes finales ni aprobar marca por inferencia.

