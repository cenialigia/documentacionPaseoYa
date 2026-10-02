---
title: "Criterio de terminado por fase"
tags: [paseoya]
status: planificado
updated: 2026-10-02
---

# Criterio de terminado por fase

Una fase pasa a **implementada** si artefactos requeridos existen y su comportamiento corresponde a decisiones vigentes. Pasa a **verificada** sólo si sus pruebas aplicables se ejecutaron con resultado y límites registrados.

- [ ] RF/RN/DEC que gobiernan la fase están identificados y aprobados donde corresponde.
- [ ] La UI cubre estados cargando, vacío, sin conexión, error, éxito y accesibilidad pertinente.
- [ ] Roles y RLS impiden leer/cambiar datos de otros comercios o clientes.
- [ ] Mutaciones críticas prueban concurrencia, idempotencia y rechazo de estados inválidos.
- [ ] Tipos, lint, pruebas, migraciones y build de la plataforma elegida se ejecutan.
- [ ] No aparecen secretos, datos reales no autorizados ni cargo económico accidental.
- [ ] Manual, arquitectura, decisiones, registro de pruebas y bitácora se actualizan.
- [ ] Handoff explica qué pasó, qué no pudo probarse y siguiente paquete.

Para F0 se exige evidencia de herramientas y dos repositorios independientes; una lista planificada no verifica su existencia. Para F1 basta revisión documental/visual del mockup con decisiones explícitas. Para F10 se exige demo funcional conforme al PDF oficial. Ninguna captura aislada acredita backend, RLS ni stock.

Si DEC-19 elige alcance B, F11 exige matriz RF-01–44/RN/RNF con resultado por requisito, incluidas operaciones de comercio/admin que F10 pueda diferir. Si elige C, F12 exige prueba de distribución, seguridad, respaldo/restauración y soporte; F13 exige UAT y aceptación del piloto. Esas fases no se cierran por haber completado la demo.
