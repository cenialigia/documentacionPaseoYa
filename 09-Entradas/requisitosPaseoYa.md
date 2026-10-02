# PaseoYa

## Plataforma de Pedidos y Marketplace del Paseo Aranjuez

**Versión:** 1.0
**Estado:** Diseño del MVP
**Tecnologías previstas:** React Native + Supabase

---

# 1. Descripción del proyecto

PaseoYa es una plataforma móvil de marketplace para los establecimientos del Paseo Aranjuez.

La aplicación permitirá que los clientes puedan descubrir establecimientos, consultar sus productos, comparar precios y disponibilidad, realizar pedidos y posteriormente acudir físicamente al Paseo Aranjuez para recoger sus compras.

El objetivo principal no es ofrecer un servicio de delivery. El modelo de PaseoYa está basado en el **pedido anticipado y retiro presencial en el establecimiento correspondiente**.

El reto plantea que los clientes puedan conocer previamente qué establecimientos existen, qué productos ofrecen, sus precios y disponibilidad, evitando tener que recorrer múltiples tiendas para encontrar un producto.

---

# 2. Objetivo general

Desarrollar un marketplace móvil que centralice la oferta de productos y servicios de los establecimientos del Paseo Aranjuez, permitiendo a los clientes:

* Descubrir establecimientos.
* Buscar productos.
* Consultar precios.
* Consultar disponibilidad.
* Comparar productos entre establecimientos.
* Crear pedidos.
* Seleccionar un método de pago.
* Recibir un código de retiro.
* Acudir al establecimiento correspondiente.
* Validar y completar el retiro de su pedido.

Los establecimientos podrán gestionar sus productos, precios, inventario y pedidos.

Los administradores podrán gestionar y supervisar la plataforma.

---

# 3. Alcance del MVP

El MVP se concentrará exclusivamente en el **Reto 3 — PaseoYa**.

No se implementarán como parte central del MVP las funcionalidades pertenecientes a:

* Paseo Points.
* Jarvis.
* Delivery externo.
* Integraciones bancarias reales.
* Sistemas comerciales reales de los establecimientos.

La documentación oficial establece que el objetivo del hackathon es desarrollar un prototipo funcional y no necesariamente un producto comercial completamente terminado.

---

# 4. Actores del sistema

El sistema tendrá tres tipos principales de usuarios.

## 4.1 Cliente

Usuario que utiliza PaseoYa para descubrir productos, realizar pedidos y recogerlos físicamente en el Paseo Aranjuez.

Puede:

* Registrarse.
* Iniciar sesión.
* Explorar establecimientos.
* Buscar productos.
* Consultar categorías.
* Consultar precios.
* Consultar disponibilidad.
* Crear y administrar carritos.
* Realizar pedidos.
* Seleccionar método de pago.
* Consultar sus pedidos.
* Consultar códigos de retiro.
* Recoger pedidos.
* Consultar historial de compras.

---

## 4.2 Comercio

Representa a un establecimiento del Paseo Aranjuez.

Puede:

* Gestionar información de su establecimiento.
* Crear productos.
* Editar productos.
* Modificar precios.
* Administrar inventario.
* Recibir pedidos.
* Confirmar pedidos.
* Preparar pedidos.
* Marcar pedidos como listos.
* Validar el retiro.
* Consultar ventas.

Las capacidades de gestión de productos, precios, inventario y pedidos forman parte del reto oficial.

---

## 4.3 Administrador

Usuario encargado de administrar la plataforma.

Puede:

* Gestionar usuarios.
* Gestionar establecimientos.
* Gestionar categorías.
* Gestionar pedidos.
* Gestionar promociones.
* Consultar estadísticas.
* Consultar ventas.
* Supervisar comportamiento general de los clientes.

Estas capacidades corresponden al rol administrativo contemplado en el reto.

---

# 5. Modelo de negocio

PaseoYa funciona como un marketplace multi-comercio.

Un mismo cliente puede interactuar con diferentes establecimientos y tener múltiples carritos activos.

Sin embargo:

> **Un pedido pertenece exclusivamente a un comercio.**

Por lo tanto, si un cliente desea comprar productos de tres establecimientos diferentes, deberá generarse un pedido independiente para cada establecimiento.

Ejemplo:

```text
Cliente
│
├── Carrito — Restaurante A
│   └── Pedido A
│
├── Carrito — Tienda B
│   └── Pedido B
│
└── Carrito — Tienda C
    └── Pedido C
```

Esto permite mantener independientes:

* Inventario.
* Preparación.
* Pago.
* Código de retiro.
* Estado del pedido.
* Fecha límite de retiro.

---

# 6. Reglas de negocio

## RN-01 — Retiro presencial

Todo pedido realizado mediante PaseoYa deberá ser recogido físicamente en el establecimiento correspondiente dentro del Paseo Aranjuez.

PaseoYa no tendrá delivery externo como mecanismo principal.

Esta condición es obligatoria dentro del reto.

---

## RN-02 — Un pedido pertenece a un comercio

Un pedido no podrá contener productos pertenecientes a diferentes establecimientos.

Si el cliente compra productos de diferentes comercios, se generarán pedidos independientes.

---

## RN-03 — Múltiples carritos

Un cliente podrá tener varios carritos activos simultáneamente.

Cada carrito estará asociado a un único comercio.

Ejemplo:

```text
Cliente
│
├── Carrito Comercio A
├── Carrito Comercio B
└── Carrito Comercio C
```

---

## RN-04 — Expiración del carrito

Cada carrito tendrá una duración máxima de:

**4 horas**

Si el cliente no completa el proceso de checkout dentro de ese período, el carrito expirará.

La expiración del carrito no deberá afectar a pedidos que ya hayan sido creados exitosamente.

---

## RN-05 — Carrito y pedido son entidades diferentes

Un carrito representa una intención temporal de compra.

Un pedido representa una operación confirmada mediante checkout.

Por lo tanto:

```text
Carrito
   │
   │ Checkout
   ▼
Pedido
```

Una vez creado el pedido, la expiración posterior del carrito no deberá cancelar ni modificar el pedido.

---

# 7. Métodos de pago

PaseoYa tendrá inicialmente dos modalidades.

## 7.1 Pago mediante QR

El cliente selecciona QR como método de pago.

Para el MVP, el pago QR será **simulado**.

No se realizará una integración bancaria real.

El flujo conceptual será:

```text
Carrito
   ↓
Checkout
   ↓
QR
   ↓
Pago simulado exitoso
   ↓
Pedido pagado
   ↓
Preparación
   ↓
Listo para recoger
   ↓
Retiro
```

---

## 7.2 Pago en efectivo

El cliente selecciona efectivo.

En este caso, el pedido funciona como una **reserva del producto**.

El cliente todavía no ha realizado el pago.

El pago se realizará físicamente al momento de recoger el pedido.

Flujo:

```text
Carrito
   ↓
Checkout
   ↓
Reserva en efectivo
   ↓
Confirmación
   ↓
Preparación
   ↓
Listo para recoger
   ↓
Cliente llega
   ↓
Pago en efectivo
   ↓
Entrega
```

---

# 8. Plazo de retiro

El plazo de retiro dependerá del método utilizado.

| Modalidad        | Plazo máximo |
| ---------------- | -----------: |
| Pago en efectivo |       3 días |
| Pago mediante QR |      14 días |

---

## RN-06 — Expiración de reserva en efectivo

Si un pedido reservado mediante efectivo no es recogido dentro de los 3 días:

1. El pedido pasa a estado `EXPIRED`.
2. La reserva queda cancelada.
3. Los productos reservados regresan al inventario disponible.
4. El cliente no recibe ningún reembolso porque todavía no había realizado el pago.

---

## RN-07 — Expiración de pedido pagado mediante QR

Si un pedido pagado mediante QR no es recogido dentro de los 14 días:

1. El pedido pasa a estado `EXPIRED`.
2. El pedido deja de estar disponible para retiro.
3. El dinero correspondiente al pedido pasa a ser propiedad del comercio.

---

# 9. Cancelación de pedidos

La cancelación dependerá del estado del pedido.

Un pedido podrá cancelarse mientras todavía no haya comenzado su preparación.

Ejemplo:

```text
CONFIRMADO
     │
     ├── CANCELAR → CANCELADO
     │
     └── PREPARAR → EN_PREPARACION
```

Una vez que el comercio ha comenzado a preparar el pedido:

```text
EN_PREPARACION
       │
       └── No se permite cancelación normal
```

---

## RN-08 — Reembolso por cancelación

Si un pedido ya pagado mediante QR es cancelado antes de comenzar su preparación:

* El pedido pasa a `CANCELLED`.
* El pago pasa a estado `REFUNDED`.
* El stock reservado vuelve a estar disponible.

En el MVP, el reembolso será simulado debido a que el sistema de pago QR no será real.

---

# 10. Inventario

El sistema deberá manejar inventario real.

Cada producto tendrá una cantidad disponible.

Ejemplo:

```text
Producto: Camiseta
Stock: 10
```

El sistema deberá evitar que dos clientes puedan comprar/reservar simultáneamente unidades que ya no están disponibles.

---

## RN-09 — Control de concurrencia

Las operaciones que modifiquen el inventario deberán realizarse de manera atómica.

El sistema deberá impedir situaciones como:

```text
Stock disponible = 1

Cliente A → compra 1
Cliente B → compra 1

Resultado incorrecto:
Stock = -1
```

El resultado esperado será:

```text
Cliente A → compra 1 → OK
Cliente B → compra 1 → RECHAZADO

Stock = 0
```

El control de concurrencia será responsabilidad principalmente de PostgreSQL/Supabase y no deberá depender exclusivamente del frontend.

---

# 11. Reserva de inventario

Para las reservas en efectivo, el sistema deberá distinguir entre:

* Stock disponible.
* Stock reservado.

Conceptualmente:

```text
Stock total
│
├── Disponible
│
└── Reservado
```

Ejemplo:

```text
Stock total:       10
Disponible:         7
Reservado:          3
```

Cuando una reserva en efectivo expire, las unidades reservadas deberán volver al stock disponible.

Cuando el cliente retire y pague el pedido:

```text
Reservado → Vendido
```

---

# 12. Estados del pedido

El pedido deberá manejar un ciclo de vida definido.

Propuesta:

```text
CREATED
   │
   ▼
CONFIRMED
   │
   ▼
IN_PREPARATION
   │
   ▼
READY_FOR_PICKUP
   │
   ▼
DELIVERED
```

También podrán existir estados alternativos:

```text
CONFIRMED
   │
   └── CANCELLED

CONFIRMED / READY_FOR_PICKUP
   │
   └── EXPIRED
```

Los estados exactos podrán convertirse posteriormente en un `enum` de PostgreSQL.

---

# 13. Estados del pago

El estado del pedido no deberá confundirse con el estado del pago.

Un pedido puede estar confirmado pero todavía no haber sido pagado.

Por ejemplo:

```text
Pedido:
CONFIRMED

Pago:
PENDING
```

Para el sistema se propone:

```text
PENDING
PAID
REFUNDED
```

Además, para pedidos QR expirados podría existir una representación específica para indicar que el dinero pasa al comercio.

La implementación definitiva se definirá durante el diseño de la base de datos.

---

# 14. Código de retiro

Cada pedido deberá generar un mecanismo de validación para que el comercio pueda verificar que la persona está autorizada a recogerlo.

El reto oficial permite utilizar diferentes mecanismos, incluyendo:

* QR.
* PIN.
* Código numérico.
* Token.

Para el MVP se utilizará preferentemente:

**QR de retiro + código de respaldo.**

Ejemplo:

```text
Pedido: #PY-10482

Código:
739251

QR:
[████████████████]
[████████████████]
[████████████████]
```

El comercio podrá escanear o validar el código.

---

# 15. Flujo completo del cliente

## 15.1 Descubrimiento

```text
Abrir aplicación
      ↓
Marketplace
      ↓
Categorías / búsqueda
      ↓
Producto
      ↓
Detalle
```

El cliente podrá consultar:

* Nombre.
* Descripción.
* Precio.
* Comercio.
* Ubicación.
* Disponibilidad.
* Información relevante del producto.

El reto contempla búsqueda global y comparación de productos ofrecidos por diferentes establecimientos.

---

## 15.2 Agregar al carrito

```text
Producto
   ↓
Seleccionar cantidad
   ↓
Agregar al carrito
```

El carrito quedará asociado al comercio correspondiente.

---

## 15.3 Checkout

```text
Carrito
   ↓
Revisar productos
   ↓
Confirmar cantidades
   ↓
Seleccionar método de pago
   ↓
Confirmar pedido
```

Dependiendo del método:

```text
QR
 ↓
Pago simulado
 ↓
Pedido pagado
```

o:

```text
Efectivo
 ↓
Reserva
 ↓
Pago pendiente
```

---

# 16. Flujo del comercio

El comercio podrá administrar su catálogo.

```text
Comercio
   │
   ├── Productos
   │     ├── Crear
   │     ├── Editar
   │     ├── Precio
   │     └── Stock
   │
   └── Pedidos
         ├── Recibido
         ├── Confirmar
         ├── Preparar
         ├── Listo
         └── Entregar
```

---

# 17. Flujo de retiro

## Pago QR

```text
READY_FOR_PICKUP
        ↓
Cliente llega
        ↓
Muestra QR de retiro
        ↓
Comercio valida
        ↓
Pedido DELIVERED
```

---

## Pago efectivo

```text
READY_FOR_PICKUP
        ↓
Cliente llega
        ↓
Comercio valida pedido
        ↓
Cliente paga efectivo
        ↓
Comercio confirma pago
        ↓
Pedido DELIVERED
```

---

# 18. Requisitos funcionales

## Autenticación

### RF-01 — Registro

El sistema deberá permitir que un usuario cree una cuenta.

### RF-02 — Inicio de sesión

El sistema deberá permitir iniciar sesión.

### RF-03 — Gestión de sesión

El sistema deberá mantener la sesión del usuario mientras corresponda.

### RF-04 — Perfil

El usuario podrá consultar y modificar su información de perfil.

---

# 19. Marketplace

### RF-05 — Listar comercios

El cliente podrá consultar los establecimientos disponibles.

### RF-06 — Consultar comercio

El cliente podrá visualizar información de un establecimiento.

### RF-07 — Listar productos

El cliente podrá consultar los productos publicados por un comercio.

### RF-08 — Categorías

El cliente podrá explorar productos mediante categorías.

### RF-09 — Búsqueda global

El cliente podrá buscar productos en todo el marketplace.

### RF-10 — Comparación

La búsqueda podrá mostrar el mismo producto o productos equivalentes ofrecidos por diferentes establecimientos, incluyendo información como precio y disponibilidad.

### RF-11 — Detalle de producto

El cliente podrá consultar el detalle de un producto.

### RF-12 — Disponibilidad

El sistema deberá mostrar si un producto tiene unidades disponibles.

---

# 20. Carritos

### RF-13 — Crear carrito

El sistema deberá crear un carrito asociado al comercio cuando el cliente agregue productos.

### RF-14 — Múltiples carritos

El cliente podrá tener múltiples carritos activos, uno por comercio.

### RF-15 — Consultar carritos

El cliente podrá visualizar todos sus carritos activos.

### RF-16 — Modificar carrito

El cliente podrá:

* Agregar productos.
* Eliminar productos.
* Modificar cantidades.

### RF-17 — Expirar carrito

El sistema deberá expirar automáticamente los carritos cuya duración haya superado las 4 horas.

---

# 21. Pedidos

### RF-18 — Crear pedido

El cliente podrá convertir un carrito en un pedido mediante checkout.

### RF-19 — Seleccionar método de pago

El cliente podrá seleccionar:

* QR.
* Efectivo.

### RF-20 — Pago QR simulado

El sistema deberá simular un pago QR exitoso.

### RF-21 — Reserva en efectivo

El sistema deberá crear una reserva cuando el cliente seleccione efectivo.

### RF-22 — Generar código de retiro

El sistema deberá generar un código de retiro único para el pedido.

### RF-23 — Consultar pedido

El cliente podrá consultar:

* Productos.
* Comercio.
* Total.
* Método de pago.
* Estado.
* Fecha de creación.
* Fecha límite de retiro.
* Código de retiro.

### RF-24 — Historial

El cliente podrá consultar sus pedidos anteriores.

### RF-25 — Cancelación

El cliente podrá cancelar un pedido cuando las reglas de negocio lo permitan.

### RF-26 — Expiración

El sistema deberá detectar y procesar automáticamente pedidos que superen su fecha límite de retiro.

---

# 22. Gestión de productos del comercio

### RF-27 — Crear producto

El comercio podrá registrar nuevos productos.

### RF-28 — Editar producto

El comercio podrá modificar información del producto.

### RF-29 — Modificar precio

El comercio podrá modificar el precio.

### RF-30 — Gestionar stock

El comercio podrá actualizar la cantidad disponible.

### RF-31 — Activar/desactivar producto

El comercio podrá controlar si un producto está disponible para los clientes.

---

# 23. Gestión de pedidos del comercio

### RF-32 — Consultar pedidos

El comercio podrá visualizar pedidos dirigidos a su establecimiento.

### RF-33 — Confirmar pedido

El comercio podrá confirmar un pedido.

### RF-34 — Preparar pedido

El comercio podrá cambiar el pedido a estado de preparación.

### RF-35 — Marcar listo

El comercio podrá marcar un pedido como listo para recoger.

### RF-36 — Validar retiro

El comercio podrá validar el código/QR de retiro.

### RF-37 — Confirmar pago en efectivo

El comercio podrá registrar el pago en efectivo al momento del retiro.

### RF-38 — Consultar ventas

El comercio podrá consultar información básica de sus ventas.

---

# 24. Administración

### RF-39 — Gestionar usuarios

El administrador podrá consultar y gestionar usuarios.

### RF-40 — Gestionar comercios

El administrador podrá gestionar los establecimientos.

### RF-41 — Gestionar categorías

El administrador podrá gestionar categorías.

### RF-42 — Supervisar pedidos

El administrador podrá consultar pedidos de la plataforma.

### RF-43 — Estadísticas

El administrador podrá consultar estadísticas generales.

### RF-44 — Promociones

El administrador podrá gestionar promociones.

Las funciones administrativas se encuentran contempladas dentro del reto oficial.

---

# 25. Requisitos no funcionales

## RNF-01 — Seguridad

La información de los usuarios deberá estar protegida mediante mecanismos de autenticación y autorización.

---

## RNF-02 — Control de acceso

Cada rol deberá tener permisos diferentes.

```text
CLIENTE
COMERCIO
ADMIN
```

Un cliente no deberá poder acceder a operaciones administrativas o de comercio.

---

## RNF-03 — Row Level Security

La base de datos deberá utilizar políticas de seguridad para garantizar que los usuarios solo puedan acceder a los datos que les corresponden.

Esto será implementado mediante las capacidades de seguridad de Supabase/PostgreSQL.

---

## RNF-04 — Integridad del inventario

Las operaciones de inventario deberán soportar concurrencia y evitar ventas superiores al stock disponible.

---

## RNF-05 — Consistencia

Las operaciones críticas deberán mantener consistencia entre:

* Pedido.
* Pago.
* Inventario.
* Reserva.

---

## RNF-06 — Trazabilidad

El sistema deberá poder determinar:

* Quién realizó un pedido.
* Qué comercio lo recibió.
* Qué productos contenía.
* Cuándo fue creado.
* Qué estado tuvo.
* Cuándo fue retirado o expiró.

---

## RNF-07 — Disponibilidad

El sistema deberá estar disponible durante la demostración del MVP y manejar adecuadamente errores de conexión.

---

## RNF-08 — Escalabilidad

La arquitectura deberá permitir agregar nuevos establecimientos y productos sin necesidad de modificar la estructura fundamental del sistema.

---

## RNF-09 — Usabilidad

La aplicación deberá permitir completar las operaciones principales con una cantidad reducida de pasos.

---

## RNF-10 — Mantenibilidad

El código deberá estar organizado de manera modular para facilitar la evolución del proyecto.

---

# 26. Casos de uso principales

## CU-01 — Registrar usuario

**Actor:** Cliente

```text
Cliente
  ↓
Ingresa datos
  ↓
Sistema valida
  ↓
Cuenta creada
```

---

## CU-02 — Buscar producto

**Actor:** Cliente

```text
Cliente
  ↓
Ingresa búsqueda
  ↓
Sistema consulta marketplace
  ↓
Muestra resultados
```

---

## CU-03 — Crear carrito

**Actor:** Cliente

```text
Cliente
  ↓
Selecciona producto
  ↓
Agrega al carrito
  ↓
Sistema crea/actualiza carrito
```

---

## CU-04 — Realizar pedido QR

**Actor:** Cliente

```text
Carrito
  ↓
Checkout
  ↓
Seleccionar QR
  ↓
Pago simulado
  ↓
Pedido pagado
  ↓
Código de retiro
```

---

## CU-05 — Realizar reserva en efectivo

**Actor:** Cliente

```text
Carrito
  ↓
Checkout
  ↓
Seleccionar efectivo
  ↓
Reserva
  ↓
Código de retiro
```

---

## CU-06 — Preparar pedido

**Actor:** Comercio

```text
Nuevo pedido
  ↓
Confirmar
  ↓
Preparar
  ↓
Listo para recoger
```

---

## CU-07 — Retirar pedido

**Actor:** Cliente + Comercio

```text
Cliente llega
  ↓
Presenta código/QR
  ↓
Comercio valida
  ↓
Pago efectivo (si corresponde)
  ↓
Pedido entregado
```

---

# 27. Expiraciones automáticas

El sistema deberá procesar automáticamente eventos relacionados con vencimientos.

## Carrito

```text
Creado
  ↓
4 horas
  ↓
EXPIRED
```

## Reserva en efectivo

```text
Creada
  ↓
3 días
  ↓
EXPIRED
  ↓
Stock liberado
```

## Pedido QR

```text
Pagado
  ↓
14 días
  ↓
EXPIRED
  ↓
Dinero queda para comercio
```

Estos procesos no deberían depender de que el usuario tenga abierta la aplicación.

La implementación concreta del mecanismo automático se definirá durante el diseño de la arquitectura de Supabase.

---

# 28. Arquitectura tecnológica prevista

La solución utilizará inicialmente:

```text
┌───────────────────────────┐
│      React Native         │
│                           │
│  Aplicación móvil         │
│  Cliente / Comercio/Admin │
└─────────────┬─────────────┘
              │
              │ API / SDK
              ▼
┌───────────────────────────┐
│         Supabase          │
│                           │
│ ┌───────────────────────┐ │
│ │ Authentication        │ │
│ ├───────────────────────┤ │
│ │ PostgreSQL            │ │
│ ├───────────────────────┤ │
│ │ Row Level Security    │ │
│ ├───────────────────────┤ │
│ │ Storage               │ │
│ ├───────────────────────┤ │
│ │ Realtime              │ │
│ └───────────────────────┘ │
└───────────────────────────┘
```

La elección de tecnologías es abierta en el reto oficial, por lo que React Native + Supabase corresponde a la decisión tecnológica del proyecto.

---

# 29. Funcionalidades fuera del MVP

Las siguientes funcionalidades podrán considerarse futuras:

* Pagos bancarios reales.
* Delivery.
* Integración con bancos.
* Sistema real de cupones.
* Recomendaciones mediante IA.
* Personalización avanzada.
* Sistema de favoritos.
* Calificaciones.
* Integración con Paseo Points.
* Integración con Jarvis.
* Integraciones comerciales externas.
* Analítica avanzada.
* Sistema de fidelización.

El documento oficial contempla varias de estas funcionalidades como extras opcionales.

---

# 30. Datos ficticios para el MVP

Los establecimientos y productos utilizados durante la demostración serán ficticios.

Ejemplo:

```text
Comercio:
TechZone

Productos:
- Audífonos Bluetooth
- Mouse inalámbrico
- Teclado mecánico
```

Esto permitirá demostrar el funcionamiento del marketplace sin depender de comercios reales.

---

# 31. Flujo general del sistema

```text
                    ┌──────────────┐
                    │    CLIENTE   │
                    └──────┬───────┘
                           │
                           ▼
                    ┌──────────────┐
                    │ Marketplace  │
                    └──────┬───────┘
                           │
                           ▼
                    ┌──────────────┐
                    │   Producto   │
                    └──────┬───────┘
                           │
                           ▼
                    ┌──────────────┐
                    │    Carrito   │
                    │    (4 h)     │
                    └──────┬───────┘
                           │
                        Checkout
                           │
                 ┌─────────┴─────────┐
                 │                   │
                 ▼                   ▼
              QR pago            EFECTIVO
              simulado           reserva
                 │                   │
                 └─────────┬─────────┘
                           │
                           ▼
                    ┌──────────────┐
                    │    PEDIDO    │
                    └──────┬───────┘
                           │
                           ▼
                    ┌──────────────┐
                    │   COMERCIO   │
                    │              │
                    │ Confirmar    │
                    │ Preparar     │
                    │ Listar       │
                    └──────┬───────┘
                           │
                           ▼
                  ┌──────────────────┐
                  │ READY_FOR_PICKUP │
                  └────────┬─────────┘
                           │
                           ▼
                    Cliente llega
                           │
                           ▼
                  Código / QR retiro
                           │
                           ▼
                  ┌──────────────────┐
                  │     RETIRO       │
                  └────────┬─────────┘
                           │
                           ▼
                       DELIVERED
```

---

# 32. MVP mínimo demostrable

Para la presentación del hackathon, el MVP deberá poder demostrar al menos:

### Cliente

* Registro/inicio de sesión.
* Marketplace.
* Comercios.
* Productos.
* Búsqueda.
* Carrito.
* Checkout.
* Pago QR simulado.
* Reserva en efectivo.
* Consulta de pedido.
* Código QR/PIN de retiro.

### Comercio

* Inicio de sesión como comercio.
* Gestión de productos.
* Gestión de stock.
* Recepción de pedidos.
* Cambio de estados.
* Validación del retiro.

### Sistema

* Inventario consistente.
* Expiración de carritos.
* Expiración de reservas.
* Expiración de pedidos.
* Diferenciación entre pago y estado del pedido.
* Control de acceso por roles.

---

# 33. Próxima etapa del proyecto

Una vez cerrado este documento de requisitos, el desarrollo se realizará en el siguiente orden:

```text
1. Requisitos
      ↓
2. Casos de uso
      ↓
3. Modelo de dominio
      ↓
4. Modelo de datos PostgreSQL
      ↓
5. ERD
      ↓
6. Diseño de RLS
      ↓
7. Arquitectura Supabase
      ↓
8. Arquitectura React Native
      ↓
9. Estructura del proyecto
      ↓
10. Implementación
      ↓
11. Pruebas
      ↓
12. Demo
```


