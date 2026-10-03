---
title: "Tareas pendientes"
tags: [paseoya]
status: planificado
updated: 2026-10-02
---

# Tareas pendientes

Casillas del plan [[05-Desarrollo/Plan por fases]]. **F0 cerrada con evidencia (2026-10-02)**; el resto sigue pendiente. El inventario SRC-04 y la planificación de esta sesión son documentación, no ejecución de fases. Marcar una casilla sólo al registrar salida y prueba en [[05-Desarrollo/Testing]] y [[06-Estado/Bitacora]].

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
- [ ] **LUI-06 / F5** *(implementado 2026-10-03: ticket QR + PIN, cancelación, simular pago; falta probar «Guardar ticket» en el dispositivo)* Pedidos en curso/historial, ticket, credencial ilustrativa, ubicación e incidencias.
- [ ] **LUI-07 / F6** *(mínimo implementado: login simulado por rol y registro de cliente; perfil y sesión real dependen de INT-01)* Acceso, cuenta y sesión por rol.
- [ ] **LUI-08 / F6** *(cola, preparación, efectivo y validación de PIN probados en EVID-DEMO-a; falta gestión de catálogo)* Vistas de comercio: catálogo, cola, preparación y retiro.
- [ ] **LUI-09 / F6** *(supervisión de sólo lectura; faltan acciones de gestión)* Vistas de administración según DEC-10/13.
- [ ] **LUI-10 / F6** Accesibilidad, dispositivos, estados vacíos/error/offline y comparación de capturas.

## Backend · F7–F9

- [x] **BE-01 / F7** *(cerrada 2026-10-03, backend `2475598`, EVID-BE-a/c)* Migraciones, Auth, membresías, RLS y pruebas de acceso directo.
- [ ] **BE-02 / F7** *(catálogo por RLS y seed listos; sin búsqueda en el servidor)* Catálogo, búsqueda/comparación y seed sintético consistente.
- [x] **BE-03 / F8** *(cerrada 2026-10-03, EVID-BE-a/b)* Carritos y checkout transaccional por comercio, pago separado, idempotencia y concurrencia de stock.
- [ ] **BE-04 / F9** *(transiciones, PIN, cancelación y `expirar_pedidos` probados; falta programar la expiración con pg_cron)* Flujo comercio, retiro QR/PIN de un uso, cancelación y expiraciones independientes del móvil.

## Integración · F10

- [ ] **INT-01** Conectar UI con contratos backend, sustituir fixtures y probar cada rol.
- [ ] **INT-02** Pruebas en dispositivo, RLS/concurrencia/expiración, manual, presentación y demo reproducible.

## Alcance B · F11, si DEC-19 lo elige

- [ ] **COMP-01** Gestión comercial completa de productos, precios, stock, horarios y ventas (RF-27–31/38).
- [ ] **COMP-02** Gestión admin, estadísticas y promociones de punta a punta (RF-39–44).
- [ ] **COMP-03** Servicios y acciones adicionales del mockup que Paulo apruebe en DEC-12/20.
- [ ] **COMP-04** Matriz de cobertura RF/RN/RNF y regresión de todos los requisitos incluidos.

## Alcance C · F12–F13, si DEC-19 lo elige

- [ ] **OPS-01** Entornos, builds/distribución, CI, migraciones reversibles y rollback.
- [ ] **OPS-02** Seguridad, rendimiento, accesibilidad, respaldo/restauración, monitoreo, privacidad y soporte.
- [ ] **PIL-01** Datos y comercios autorizados, capacitación y UAT por rol.
- [ ] **PIL-02** Salida controlada, observación, corrección y aceptación del piloto.

**Puertas críticas:** ver [[Decisiones de Usuario para el desarrollo]]. DEC-19 determina si el denominador activo son 19 lotes para demo, 23 para cobertura funcional o 27 para piloto. Las decisiones restantes sólo bloquean los lotes dependientes; no se inventa una respuesta por el mockup. Ideas futuras como Points, Jarvis, delivery o IA permanecen fuera del MVP.
