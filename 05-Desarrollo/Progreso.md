---
title: "Progreso inicial"
tags: [paseoya]
status: planificado
updated: 2026-10-02
---

# Progreso del plan UI/backend

Derivado de las 27 casillas potenciales de [[06-Estado/Tareas pendientes]] y los resultados de [[05-Desarrollo/Testing]], a fecha 2026-10-02. El denominador activo depende de [[Decisiones de Usuario para el desarrollo|DEC-19]]. No es telemetría de código.

- **Trabajo implementado para demo A:** 4/19 casillas cerradas = **21,1 %**. Distribución: F0 3/3, UI 1/10, backend 0/4, integración 0/2. Las tres casillas son preparación del entorno: todavía no hay código de producto.
- **Alcance B/C aún no activado:** +4/+8 casillas; serían 0/23 o 0/27 si Paulo elige ese objetivo. No sumar tareas condicionales al progreso de demo.
- **Trabajo probado:** F0 completa con T-F0 PASS (EVID-F0-01 a 03e: inventario, repositorios, Expo en emulador, Supabase local con migración y push). Las otras 14 pruebas planificadas están `NO_EJECUTADA` por falta de código de producto o por fases condicionales; no se calcula un porcentaje de aprobación runtime del producto.
- Documentación de planificación: mockup SRC-04 preservado e incrustado; fases y lotes redactados. Esta salida no cierra F0 ni LUI-01: dirección visual y conflictos requieren decisión.
- Decisiones materiales: DEC-01–16 y DEC-18–25 pendientes según la fase; DEC-17 resuelta por RN-02/03. ADR-008 registra la separación de repositorios solicitada.
- **LUI-01:** cerrada con la aprobación de DEC-11 (EVID-LUI-01b). Es una especificación documental: todavía no hay pantallas implementadas.
- **LUI-02:** shell implementado y probado en el emulador (EVID-LUI-02a); la casilla sigue abierta hasta la prueba de accesibilidad con TalkBack. No suma al porcentaje.
- Próximo paso: cerrar LUI-02 con TalkBack y texto al 200 %; después LUI-03 (Explorar, tienda, detalle y comparación con filtros), con DEC-09 pendiente para la equivalencia de productos.
- Separación de progreso: documentación de planificación ≠ implementación ≠ funcionamiento probado.

Actualizar esta nota desde casillas reales del plan y resultados de pruebas; no estimar porcentajes desde sensación. Si una prueba no es ejecutable por falta de entorno, listar su motivo sin contarla como aprobada.
