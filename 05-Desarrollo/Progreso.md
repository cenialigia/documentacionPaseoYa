---
title: "Progreso inicial"
tags: [paseoya]
status: en_desarrollo
updated: 2026-10-03
---

# Progreso del plan UI/backend

Derivado de [[06-Estado/Tareas pendientes]] y [[05-Desarrollo/Testing]], a 2026-10-03. No es telemetría de código actual: el frontend/backend se trabajaron en otro equipo y sus commits vigentes se inventarían en F14-00.

| Alcance | Cerrado | Abierto o límite |
| --- | --- | --- |
| Demo A (DEC-19) | **13/19 lotes = 68,4 %**: F0 3/3; UI 6/10 (LUI-01/03/04/05/06/08); backend 3/4 (BE-01/03/04); integración 1/2 (INT-01). | LUI-02 TalkBack manual, LUI-07 recuperación/perfil, LUI-09 gestión admin, LUI-10 revisión final, BE-02 búsqueda servidor, INT-02 presentación. |
| Cobertura B / piloto C | No activados como objetivo de esta demo. | F11 añade 4 lotes; F12–13 añaden otros 4. No contarlos como cerrados por el prototipo. |
| F14 ampliación por nuevos PDF y mockups | **Lote Cliente:** F14-00 completo, X-01/02/03 y BE-01/07 cerrados con EVID-F14-CLI-a y EVID-F14-BE-a (X-04 parcial); **Lote Comercio:** BE-04/05 cerrados y X-05 parcial con EVID-F14-BE-b y EVID-F14-COM-a; **Lote Admin:** BE-06 y X-06 cerrados con EVID-F14-BE-c y EVID-F14-ADM-a; X-04 y X-05 cerrados con EVID-F14-CLI-b y EVID-F14-COM-b (QR leído con la cámara del teléfono); antes: 0 cerradas; 54 recortes, 6 tareas de vistas/estados sin recorte, 7 de backend y 4 de QA propuestas. | Puerta F14-00 y [[02-Arquitectura/Decisiones F14 antes de iniciar]] pendientes; estados F14 `NO_EJECUTADA`. No se añade F14 al denominador de la demo A. |

**Evidencia anterior:** demo integrada con Supabase en emulador y dos dispositivos reales en tiempo real (EVID-INT-01a, EVID-INT-02a/b); backend 17/17 pruebas SQL, acceso por rol, concurrencia real, Realtime y pg_cron (EVID-BE-a/b/c/d). Catálogo del comercio y stock concurrente EVID-LUI-08a; carrito persistente EVID-CART-a. Estas pruebas sustentan la clasificación `SUP`, no prueban por sí mismas todas las vistas F14.

**Próximas acciones independientes:** completar presentación de INT-02 y TalkBack de LUI-02; al abrir F14, revisar commits y decisiones primero. Actualizar porcentajes sólo al cerrar casillas con evidencia PASS y límite declarado; si falta entorno, registrar `NO_EJECUTADA`.
