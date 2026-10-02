---
title: "Decisiones técnicas y autoridad"
tags: [paseoya]
status: planificado
updated: 2026-10-02
---

# Decisiones técnicas y autoridad

| ID | Estado | Decisión / fundamento | Revisión |
| --- | --- | --- | --- |
| ADR-001 | Elegida inicialmente por Paulo | App móvil con React Native; el PDF permite libertad tecnológica (§8). | Variante Expo o bare, versiones, plataforma de demo: DEC-01 |
| ADR-002 | Elegida inicialmente por Paulo | Supabase con PostgreSQL relacional como base; Auth/RLS/Storage y automatizaciones son posibilidades de diseño, no servicios configurados. | Proyecto, región, cuotas y mecanismo de operaciones críticas: DEC-02 |
| ADR-003 | Regla del reto | Retiro presencial obligatorio; no orientar la app a delivery (PDF §5.6). | No desplazar al agregar mejoras |
| ADR-004 | Requisito aportado por Paulo (MD v1) | Checkout con QR simulado y efectivo; el documento oficial menciona pagos habilitados y valora QR como adicional. | Flujos/estados y demostración: DEC-04/05 |
| ADR-007 | Requisito aportado por Paulo (MD v1) | Carritos independientes y un pedido por comercio (RN-02/03); no requiere reconfirmación de la regla. | Operación de checkout en F8 y experiencia visual en F4 |
| ADR-005 | Propuesta de seguridad | No confiar al cliente móvil un checkout de varias escrituras o reserva de stock. Transacción controlada en PostgreSQL / backend de confianza, con autorización comprobada. | Diseño concreto y pruebas de concurrencia: DEC-02 |
| ADR-006 | Propuesta visual | Bocetos de navegación y jerarquía en [[02-Arquitectura/Wireframes iniciales]]. | Dirección estética y revisión del propietario: DEC-11 |
| ADR-008 | Solicitada por Paulo en SRC-05 | Código cliente React Native y backend Supabase en **dos repositorios Git separados**; el Core documental queda fuera de ambos. | F0 verifica/crea las raíces; remotos, Expo/bare y proyecto Supabase requieren DEC-01/02. |

Las ADR fijan autoridad y alcance, no declaran implementación. SRC-04 aporta [[02-Arquitectura/Mockup Stitch - vistas y ubicaciones|mockups]] para UI, sin aprobar pagos reales, reservas de stock ni la paleta final. El diseño de schema, RLS, funciones SQL, librerías, proveedor de notificaciones y automatizador de expiración siguen abiertos. Registrar cada cierre futuro con fecha, opciones, consecuencias, aprobador y evidencia.
