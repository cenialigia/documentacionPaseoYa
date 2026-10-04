---
title: "Decisiones técnicas y autoridad"
tags: [paseoya]
status: planificado
updated: 2026-10-02
---

# Decisiones técnicas y autoridad

| ID | Estado | Decisión / fundamento | Revisión |
| --- | --- | --- | --- |
| ADR-001 | Elegida inicialmente por Usuario | App móvil con React Native; el PDF permite libertad tecnológica (§8). | Variante Expo o bare, versiones, plataforma de demo: DEC-01 |
| ADR-002 | Elegida inicialmente por Usuario | Supabase con PostgreSQL relacional como base; Auth/RLS/Storage y automatizaciones son posibilidades de diseño, no servicios configurados. | Proyecto, región, cuotas y mecanismo de operaciones críticas: DEC-02 |
| ADR-003 | Regla del reto | Retiro presencial obligatorio; no orientar la app a delivery (PDF §5.6). | No desplazar al agregar mejoras |
| ADR-004 | Requisito aportado por Usuario (MD v1) | Checkout con QR simulado y efectivo; el documento oficial menciona pagos habilitados y valora QR como adicional. | Flujos/estados y demostración: DEC-04/05 |
| ADR-007 | Requisito aportado por Usuario (MD v1) | Carritos independientes y un pedido por comercio (RN-02/03); no requiere reconfirmación de la regla. | Operación de checkout en F8 y experiencia visual en F4 |
| ADR-005 | Propuesta de seguridad | No confiar al cliente móvil un checkout de varias escrituras o reserva de stock. Transacción controlada en PostgreSQL / backend de confianza, con autorización comprobada. | Diseño concreto y pruebas de concurrencia: DEC-02 |
| ADR-006 | Propuesta visual | Bocetos de navegación y jerarquía en [[02-Arquitectura/Wireframes iniciales]]. | Dirección estética y revisión del propietario: DEC-11 |
| ADR-012 | DEC-F14-01–16, 2026-10-03 | F14 progresivo Cliente → Comercio → Admin; barras del PDF por rol; QR de pago simulado con pantalla y cuenta atrás; DEC-16 se mantiene; favoritos y notificaciones; registro con teléfono/género/nacimiento y avatar; recuperación de contraseña; promociones % con aprobación admin; tuteo y datos de mosaicos; escáner con cámara + PIN; entrega en dos pasos atómica; tabla de categorías; Storage para imágenes. | Ver [[02-Arquitectura/Decisiones F14 antes de iniciar]]; DEC-24 pendiente |
| ADR-011 | DEC-03/04/05/06/07/08/09/10/16/19/20, 2026-10-03 | Roles CLIENTE/COMERCIO/ADMIN con un rol por usuario y autorización en backend; misma app por rol; stock atómico al confirmar; plazos en tiempo corrido (La Paz); pago QR simulado con «Simular pago»; QR+PIN de un uso; sin función Comparar (búsqueda); extras: guardar ticket y reportar problema; cancelación del cliente sólo en Confirmado; QR vencido = Expirado/retenido por el comercio; objetivo A con entrega en menos de 1 día. | Schema, RLS y funciones en BE-01–04; recorte por plazo en el Plan por fases |
| ADR-010 | DEC-11/15, 2026-10-03 | Sistema visual de [[02-Arquitectura/Especificacion UI LUI-01]]: tokens M3 de Stitch, Plus Jakarta Sans, iconos Material, tema claro, 48 dp, usted, logo de texto provisional y placeholders sin marca. | Logo definitivo, tema oscuro e imágenes reales quedan para decisiones posteriores |
| ADR-009 | DEC-01/02, 2026-10-02 | Cliente con **Expo SDK 57 (RN 0.86) y Expo Router, Android primero**. Backend con **Supabase CLI local sobre Docker**, versionado en `backend/`; sin servidor Node adicional ni proyecto cloud. | Proyecto cloud, propietario y región pendientes de DEC-02; iOS sale del alcance de la primera entrega |
| ADR-008 | Solicitada por Usuario en SRC-05 | Código cliente React Native y backend Supabase en **dos repositorios Git separados**; el Core documental queda fuera de ambos. | F0 verifica/crea las raíces; remotos, Expo/bare y proyecto Supabase requieren DEC-01/02. |

Las ADR fijan autoridad y alcance, no declaran implementación. SRC-04 aporta [[02-Arquitectura/Mockup Stitch - vistas y ubicaciones|mockups]] para UI, sin aprobar pagos reales, reservas de stock ni la paleta final. El diseño de schema, RLS, funciones SQL, librerías, proveedor de notificaciones y automatizador de expiración siguen abiertos. Registrar cada cierre futuro con fecha, opciones, consecuencias, aprobador y evidencia.
