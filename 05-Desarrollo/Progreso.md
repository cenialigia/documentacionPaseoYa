---
title: "Progreso inicial"
tags: [paseoya]
status: planificado
updated: 2026-10-02
---

# Progreso del plan UI/backend

Derivado de las 27 casillas potenciales de [[06-Estado/Tareas pendientes]] y los resultados de [[05-Desarrollo/Testing]], a fecha 2026-10-02. El denominador activo depende de [[Decisiones de Usuario para el desarrollo|DEC-19]]. No es telemetría de código.

- **Trabajo implementado para demo A:** 2/19 casillas cerradas = **10,5 %**. Distribución: F0 2/3, UI 0/10, backend 0/4, integración 0/2. Las dos casillas son preparación del entorno: todavía no hay código de producto.
- **Alcance B/C aún no activado:** +4/+8 casillas; serían 0/23 o 0/27 si Paulo elige ese objetivo. No sumar tareas condicionales al progreso de demo.
- **Trabajo probado:** 2 lotes con evidencia PASS (EVID-F0-01/02, inventario y separación de repositorios). T-F0 sigue abierta: F0-03 tiene su parte estática y la publicación en PASS, Supabase local y migración de prueba en PASS (EVID-F0-03e); sólo falta la ejecución en dispositivo, que está `NO_EJECUTADA`. Las otras 14 pruebas planificadas están `NO_EJECUTADA` por falta de código/entorno o por fases aún condicionales; por ello no se calcula porcentaje de aprobación runtime.
- Documentación de planificación: mockup SRC-04 preservado e incrustado; fases y lotes redactados. Esta salida no cierra F0 ni LUI-01: dirección visual y conflictos requieren decisión.
- Decisiones materiales: DEC-01–16 y DEC-18–25 pendientes según la fase; DEC-17 resuelta por RN-02/03. ADR-008 registra la separación de repositorios solicitada.
- Próximo paso: cerrar **F0-03** arrancando la app en un emulador o dispositivo (EVID-F0-03b). DEC-01/02 ya están resueltas (ADR-009). LUI-01 (revisión visual y MK-01–08) puede avanzar en paralelo.
- Separación de progreso: documentación de planificación ≠ implementación ≠ funcionamiento probado.

Actualizar esta nota desde casillas reales del plan y resultados de pruebas; no estimar porcentajes desde sensación. Si una prueba no es ejecutable por falta de entorno, listar su motivo sin contarla como aprobada.
