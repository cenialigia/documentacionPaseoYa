---
title: "Reglas de negocio y estados"
tags: [paseoya]
status: planificado
updated: 2026-10-02
---

# Reglas de negocio y estados

Fuente primaria del retiro: SRC-01 PDF §5.6. Las RN-02–09 son requisitos expresos del MD SRC-02 aportado por Usuario; conservar sus IDs. Sólo sus detalles ambiguos o con efecto externo requieren una decisión adicional.

| ID | Regla | Validación pendiente / prueba |
| --- | --- | --- |
| RN-01 | Retiro presencial en el establecimiento; no delivery principal | PDF obligatorio; T-RET |
| RN-02 | Cada pedido corresponde a un único comercio | solicitado; T-ORD |
| RN-03 | Un cliente puede tener carritos simultáneos, uno por comercio | solicitado; T-CART |
| RN-04 | Carrito vence tras 4 horas sin checkout | inicio/zona DEC-06; T-EXP |
| RN-05 | Carrito y pedido son entidades distintas; expirar carrito no altera pedido | T-CART |
| RN-06 | Reserva en efectivo no recogida en 3 días expira y libera stock | DEC-05/06; T-EXP |
| RN-07 | Pedido QR simulado no recogido en 14 días expira; texto del MD dice que dinero pasa al comercio | DEC-07: **no modelar transferencia real**; T-EXP |
| RN-08 | Cancelación antes de preparación; reembolso QR y liberación simulados | DEC-08; T-CAN |
| RN-09 | Inventario con concurrencia atómica, nunca stock negativo | DEC-05; T-STOCK |

Estados de pedido candidatos: `CREATED → CONFIRMED → IN_PREPARATION → READY_FOR_PICKUP → DELIVERED`; salidas `CANCELLED` o `EXPIRED`. Estados de pago candidatos: `PENDING`, `PAID`, `REFUNDED`. Son **dos máquinas distintas**. Identidad de orden, caducidad, reintentos, idempotencia y auditoría se fijan antes de SQL.

Requisito crítico adicional: validar credencial de retiro sólo una vez, por personal autorizado del comercio dueño; T-RET. Plantilla para reglas futuras: [[04-Reglas-de-negocio/_Plantilla de regla]].
