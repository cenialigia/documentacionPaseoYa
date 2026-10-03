---
title: "Preparación de demo y operación"
tags: [paseoya]
status: planificado
updated: 2026-10-02
---

# Preparación de demo y operación

Objetivo decidido: **A · demo de hackathon** ([[Decisiones de Usuario para el desarrollo|DEC-19]]), con entrega en menos de 1 día (DEC-03). El PDF §9 pide prototipo, código fuente, presentación, demostración en vivo y explicación de frontend, backend, base, APIs, IA si aplica y servicios externos.

| Entregable | Preparación | Estado |
| --- | --- | --- |
| Prototipo funcional | recorrido cliente→comercio→retiro, QR simulado y efectivo | **Listo**: app conectada a Supabase, probada en emulador y teléfono (EVID-INT-02b) |
| Código fuente | repositorio/proyecto reproducible y migraciones de datos ficticios | **Listo**: `cenialigia/PaseoYaFrontend` y `cenialigia/PaseoYaBackend` (migraciones, seed, pruebas) |
| Presentación | problema, usuarios, valor, funcionamiento, stack y proyección real | Pendiente (equipo) |
| Demo en vivo | dispositivo, cuentas de roles, datos seed, conectividad y plan de contingencia | **Listo**: guion de dos dispositivos y cuentas en el README del frontend; `npm run db:reset` restaura el seed; contingencia: conexión por USB con `adb reverse` (sin depender del Wi-Fi) |
| Arquitectura | React Native, Supabase/PostgreSQL, RLS, operaciones críticas y servicios usados | **Implementada**: Expo SDK 57 + Supabase local (Auth, PostgREST, RLS, funciones SECURITY DEFINER, Realtime, pg_cron); ver [[02-Arquitectura/Decisiones tecnicas]] ADR-009–011 |

Antes de una demo real: confirmar propietario de cuentas, restaurar entorno, probar flujo y expiraciones, respaldo mínimo de datos demo, revisar costes/cuotas y secretos, ensayar desconexión. Producción comercial, pagos reales, políticas legales y despliegue continuo requieren decisiones nuevas; no se presuponen.

**Manual:** [[07-Manuales/Manual de usuario]] (verificado contra la app el 2026-10-03).
