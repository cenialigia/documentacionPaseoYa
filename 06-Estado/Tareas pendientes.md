---
title: "Tareas pendientes"
tags: [paseoya]
status: planificado
updated: 2026-10-03
---

# Tareas pendientes

Casillas del plan [[05-Desarrollo/Plan por fases]]. **F0 y otros 10 lotes de demo cerrados con evidencia; total 13/19** según [[05-Desarrollo/Progreso]]. F14 sólo está documentada. Marcar una casilla al registrar salida, prueba y límite en [[05-Desarrollo/Testing]] y [[06-Estado/Bitacora]].

## F0 · Preparación técnica

- [x] **F0-01** (EVID-F0-01) Verificar existencia y versiones compatibles de Node.js, gestor, React Native/Expo o bare según DEC-01, Android/iOS elegido, emulador/dispositivo y Supabase CLI; registrar faltantes.
- [x] **F0-02** (EVID-F0-02: `frontend/` y `backend/`, remotos `cenialigia/PaseoYaFrontend` y `cenialigia/PaseoYaBackend`) Crear o verificar `PaseoYA-frontend/` y `PaseoYA-backend/` como **dos repositorios Git independientes**, sin meter `PaseoYA-Core/` en ninguno; registrar rutas/remotos autorizados.
- [x] **F0-03** (EVID-F0-03a–e: Expo SDK 57 en emulador, Supabase local con migración de prueba, push verificado) Inicializar cliente y backend Supabase reproducibles según DEC-01/02; ejemplos de variables sin secretos, migración local de prueba y arranque mínimo.

## UI · F1–F6

- [x] **LUI-01 / F1** *(cerrada 2026-10-03: [[02-Arquitectura/Especificacion UI LUI-01]] aprobada en DEC-11; EVID-LUI-01a/b)* Cerrar inventario visual, tokens, rutas, copy, assets/licencias, estados y conflictos MK-01–08 de [[02-Arquitectura/Mockup Stitch - vistas y ubicaciones]].
- [ ] **LUI-02 / F2** *(implementado 2026-10-03; EVID-LUI-02a/b PASS, incluido el texto al 200 %; falta una pasada manual con TalkBack, EVID-LUI-02c)* Shell React Native, cuatro pestañas cliente, stacks, tema, componentes y fixtures coherentes.
- [x] **LUI-03 / F3** *(cerrada 2026-10-03: DEC-09 retiró la comparación; pestaña Buscar, EVID-LUI-03a)* Explorar, tiendas, ofertas, detalle faltante, búsqueda/comparación y filtros.
- [x] **LUI-04 / F4** *(cerrada 2026-10-03: DEC-05/06 aplicadas, EVID-LUI-04a + EVID-DEMO-a)* Carritos separados, cantidades, subtotal, temporizador y expiración visual.
- [x] **LUI-05 / F4** *(cerrada 2026-10-03: DEC-04/05/06 aplicadas, EVID-LUI-05a + EVID-DEMO-a)* Checkout por comercio, QR **simulado**/efectivo, condiciones y errores/reintentos.
- [x] **LUI-06 / F5** *(cerrada 2026-10-03: ticket QR + PIN, «Guardar ticket», cancelación y actualización en tiempo real; EVID-DEMO-a, EVID-INT-02a/b)* Pedidos en curso/historial, ticket, credencial ilustrativa, ubicación e incidencias.
- [ ] **LUI-07 / F6** *(login, sesión y registro Supabase probados en EVID-INT-01a/02a; recuperación de contraseña y edición de perfil siguen abiertas)* Acceso, cuenta y sesión por rol.
- [x] **LUI-08 / F6** *(cerrada 2026-10-03: catálogo propio (RF-27–31) con stock protegido frente a ventas concurrentes, cola, preparación, efectivo y PIN; EVID-LUI-08a, EVID-DEMO-a, EVID-INT-02b; frontend `cf9c9da`)* Vistas de comercio: catálogo, cola, preparación y retiro.
- [ ] **LUI-09 / F6** *(supervisión de sólo lectura; faltan acciones de gestión)* Vistas de administración según DEC-10/13.
- [ ] **LUI-10 / F6** Accesibilidad, dispositivos, estados vacíos/error/offline y comparación de capturas.

## Backend · F7–F9

- [x] **BE-01 / F7** *(cerrada 2026-10-03, backend `2475598`, EVID-BE-a/c)* Migraciones, Auth, membresías, RLS y pruebas de acceso directo.
- [ ] **BE-02 / F7** *(catálogo por RLS y seed listos; sin búsqueda en el servidor)* Catálogo, búsqueda/comparación y seed sintético consistente.
- [x] **BE-03 / F8** *(cerrada 2026-10-03, EVID-BE-a/b)* Carritos y checkout transaccional por comercio, pago separado, idempotencia y concurrencia de stock.
- [x] **BE-04 / F9** *(cerrada 2026-10-03: transiciones, PIN, cancelación y expiración con pg_cron; EVID-BE-a/d; `45b0e3e` publicado según bitácora)* Flujo comercio, retiro QR/PIN de un uso, cancelación y expiraciones independientes del móvil.

## Integración · F10

- [x] **INT-01** *(cerrada 2026-10-03, frontend `146c16a`, EVID-INT-01a)* Conectar UI con contratos backend, sustituir fixtures y probar cada rol.
- [ ] **INT-02** *(pruebas en emulador y en teléfono físico, RLS/concurrencia/expiración, manual y guion de demo listos (EVID-INT-02a/b); falta la presentación del hackathon)* Pruebas en dispositivo, RLS/concurrencia/expiración, manual, presentación y demo reproducible.

## Alcance B · F11 · cerrada 2026-10-04 ([[05-Desarrollo/F11 - Matriz de requisitos]])

- [x] **COMP-01** Gestión comercial completa de productos, precios, stock, horarios y ventas (RF-27–31/38).
- [x] **COMP-02** Gestión admin, estadísticas y promociones de punta a punta (RF-39–44).
- [x] **COMP-03** Servicios y acciones adicionales del mockup que Usuario apruebe en DEC-12/20. *(Aprobados y hechos en F14: avisos, favoritos, promociones, cámara; el resto quedó fuera por DEC-20/DEC-F14-05.)*
- [x] **COMP-04** Matriz de cobertura RF/RN/RNF y regresión de todos los requisitos incluidos. *(RF 42/44 PASS y 2 parciales con límite; RN 13/13; RNF 9/10; huecos listados en la matriz.)*

## Alcance C · F12–F13, si DEC-19 lo elige

- [ ] **OPS-01** Entornos, builds/distribución, CI, migraciones reversibles y rollback.
- [ ] **OPS-02** Seguridad, rendimiento, accesibilidad, respaldo/restauración, monitoreo, privacidad y soporte.
- [ ] **PIL-01** Datos y comercios autorizados, capacitación y UAT por rol.
- [ ] **PIL-02** Salida controlada, observación, corrección y aceptación del piloto.

## F14 · Revisión y ampliación por roles · cerrada para la demo (2026-10-04)

- [x] **F14-00.0–00.3** Comprobación conjunta de cambios/commits del Core, frontend y backend con el agente asignado; después inventario del código y preguntas/decisiones de [[02-Arquitectura/Decisiones F14 antes de iniciar]] antes de implementar cada lote afectado.
- [x] **F14-UI-C** 26 tareas `F14-CLI-01`–`26`, cada una con captura y ubicación en [[02-Arquitectura/F14 - Cliente - vistas y tareas]].
- [x] **F14-UI-M** 14 tareas `F14-COM-01`–`14` en [[02-Arquitectura/F14 - Comercio - vistas y tareas]].
- [x] **F14-UI-A** 14 tareas `F14-ADM-01`–`14` en [[02-Arquitectura/F14 - Administrador - vistas y tareas]].
- [x] **F14-UI-X** 6 tareas `F14-X-01`–`06` para rutas/estados exigidos por los PDF sin cuadro independiente, en [[05-Desarrollo/F14 - Revision y ampliacion por roles]].
- [x] **F14-BE-01–07** Identidad, búsqueda, compra/reserva, retiro por cámara, comercio, administración y extras condicionales, descritos en [[05-Desarrollo/F14 - Revision y ampliacion por roles]].
- [x] **F14-QA-01–04** Matriz de trazabilidad, dispositivo/accesibilidad, seguridad/concurrencia y comparación visual; evidencia en [[05-Desarrollo/Testing]] y [[05-Desarrollo/F14 - Matriz QA]].
- [ ] **F14-QA-02 (resto)** TalkBack y texto al 200 % en el dispositivo: los activa el usuario; hasta entonces `NO_EJECUTADA`.

**Puertas críticas:** ver [[Decisiones de Usuario para el desarrollo]]. DEC-19 determina si el denominador activo son 19 lotes para demo, 23 para cobertura funcional o 27 para piloto. Las decisiones restantes sólo bloquean los lotes dependientes; no se inventa una respuesta por el mockup. Ideas futuras como Points, Jarvis, delivery o IA permanecen fuera del MVP.

## Orden de trabajo después de la demo (2026-10-04)

La demo pasó; se retoma el flujo F11 → F12 → F13, reordenado según lo que ya existe.

1. **F11 · Cobertura funcional** — cerrada: matriz de requisitos, trazabilidad (RNF-06), rechazo del comercio (DEC-F11-01) y stock reservado visible (§11).
2. **F12 · Preparación para uso real**, en este orden:
   - [ ] **OPS-01a** Separar ambientes: proyecto Supabase de pruebas distinto del de producción, perfiles de EAS por ambiente y aplicar las migraciones F11 primero en pruebas.
   - [ ] **OPS-02a** Correo propio (SMTP) para la recuperación de contraseña por código y otros avisos por correo.
   - [ ] **OPS-01b** CI: tipos, lint y pruebas SQL en cada cambio; migraciones reversibles documentadas.
   - [ ] **OPS-02b** Restauración ensayada de un respaldo, monitoreo de errores y revisión de seguridad.
   - [ ] **OPS-02c** Accesibilidad: TalkBack y texto al 200 % (activa el usuario); paginación de búsquedas.
   - [ ] **OPS-01c** Distribución (DEC-23): titular de cuentas, build firmado para tienda o APK interno, costes.
3. **F13 · Piloto** — requiere DEC-25 (comercios, dispositivos, volumen y metas) y lo pendiente de DEC-24 (responsables, criterio de pausa).

Mejoras sin decisión registradas en [[05-Desarrollo/F14 - Matriz QA]] (filas compactas, gráficos de línea, avisos de promociones al cliente) quedan para cuando se priorice diseño.
