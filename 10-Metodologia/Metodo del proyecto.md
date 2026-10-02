---
title: "Método del proyecto y agentes"
tags: [paseoya]
status: planificado
updated: 2026-10-02
---

# Método del proyecto y agentes

1. Entrar por [[00-Inicio]], leer contrato raíz y [[01-Contexto/Contexto activo]].
2. Fijar P-ID, RF/RN/DEC, resultado y prueba antes de trabajar. Cargar sólo módulo, regla, fuente y artefactos afectados.
3. Contrastar documentación con código y migraciones reales; si divergen, registrar conflicto sin sobrescribir intención.
4. Resolver con Paulo decisiones de alcance, pago, datos, permisos y UI que cambien el resultado. No instalar skills o conectar servicios por recomendación documental.
5. Entregar una fase verificable. Proteger operaciones críticas en servidor/BD; no confiar en controles del móvil para RLS o stock.
6. Cerrar con test observado o NO_EJECUTADA, bitácora, manual afectado, progreso y siguiente paquete.
7. Aceptar trabajo de especialistas sólo tras revisión del integrador; no repartir la misma migración o cambio con efecto entre dos agentes. No inferir soporte de una skill para Claude/Codex por existir el archivo.
8. Promover aprendizajes reutilizables a un cerebro sólo mediante retrospectiva con evidencia, aprobación y versión. El cerebro de dominio de esta app está sin asignar.

**Eficiencia multiagente:** medir criterio verificado por sesión, lecturas repetidas y retrabajo. Tokens de entrada/salida/caché/razonamiento sólo si el proveedor expone datos comparables; si no, `null`. No perseguir ahorro que pierda pruebas. No guardar prompts íntegros, secretos ni razonamiento privado. Usar skills existentes sólo cuando reducen trabajo o riesgo; antes de instalar una nueva, auditar permisos/datos y consultar a Paulo. Un LLM no forma parte de la app salvo decisión futura.

