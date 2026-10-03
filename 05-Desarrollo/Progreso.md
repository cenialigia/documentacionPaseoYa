---
title: "Progreso inicial"
tags: [paseoya]
status: planificado
updated: 2026-10-02
---

# Progreso del plan UI/backend

Derivado de las 27 casillas potenciales de [[06-Estado/Tareas pendientes]] y los resultados de [[05-Desarrollo/Testing]], a fecha 2026-10-02. El denominador activo depende de [[Decisiones de Usuario para el desarrollo|DEC-19]]. No es telemetría de código.

- **Trabajo implementado para demo A (DEC-19 = A):** 11/19 casillas cerradas = **57,9 %**. Distribución: F0 3/3, UI 4/10 (LUI-01/03/04/05), backend 3/4 (BE-01/03/04), integración 1/2 (INT-01). Implementados pero abiertos: LUI-02 (TalkBack manual), LUI-06 («Guardar ticket» sin prueba), LUI-07/08/09 mínimos, BE-02 (sin búsqueda en el servidor) e INT-02 (pruebas por dispositivo, manual y demo).
- **Alcance B/C aún no activado:** +4/+8 casillas; serían 0/23 o 0/27 si Paulo elige ese objetivo. No sumar tareas condicionales al progreso de demo.
- **Trabajo probado:** la app conectada a Supabase recorre la demo completa con los tres roles (EVID-INT-01a); backend con 17/17 pruebas SQL, concurrencia real, login por API, Realtime y pg_cron (EVID-BE-a/b/c/d).
- Documentación de planificación: mockup SRC-04 preservado e incrustado; fases y lotes redactados. Esta salida no cierra F0 ni LUI-01: dirección visual y conflictos requieren decisión.
- Decisiones materiales: DEC-01–16 y DEC-18–25 pendientes según la fase; DEC-17 resuelta por RN-02/03. ADR-008 registra la separación de repositorios solicitada.
- **LUI-01:** cerrada con la aprobación de DEC-11 (EVID-LUI-01b). Es una especificación documental: todavía no hay pantallas implementadas.
- **LUI-02:** implementado; accesibilidad automática y texto al 200 % en PASS (EVID-LUI-02b). Abierta sólo por la pasada manual con TalkBack (EVID-LUI-02c `NO_EJECUTADA`).
- **LUI-03:** implementado y probado en el emulador (EVID-LUI-03a); abierto hasta DEC-09 (equivalencia en la comparación).
- **LUI-04:** implementado y probado en el emulador (EVID-LUI-04a); abierto hasta DEC-05/06.
- **LUI-05:** implementado y probado en el emulador (EVID-LUI-05a): idempotencia ante respuesta perdida y doble toque con el servicio simulado; abierto hasta DEC-04/05/06. Los lotes LUI-02 a 05 no suman todavía al porcentaje, porque cada uno espera una decisión o una prueba manual.
- Próximo paso: publicar el commit `45b0e3e` del backend (requiere confirmación); INT-02: ensayo en un teléfono físico con la IP del equipo, observar Realtime entre dos dispositivos y probar «Guardar ticket» y el registro.
- Separación de progreso: documentación de planificación ≠ implementación ≠ funcionamiento probado.

Actualizar esta nota desde casillas reales del plan y resultados de pruebas; no estimar porcentajes desde sensación. Si una prueba no es ejecutable por falta de entorno, listar su motivo sin contarla como aprobada.
