---
title: "Entorno local previsto"
tags: [paseoya]
status: planificado
updated: 2026-10-02
---

# Entorno local previsto

No existe proyecto React Native ni Supabase configurado en esta raíz al crear la semilla. SRC-05 pide planificar **F0** para verificar Node.js, gestor de paquetes, toolchain React Native, plataforma de prueba y CLI/entorno Supabase. Versiones, Expo/bare y comandos se fijan en F0/DEC-01–02 después de comprobar compatibilidad actual. Ver [[05-Desarrollo/Plan por fases]].

Topología operativa solicitada: `PaseoYA-frontend/` y `PaseoYA-backend/` como repositorios Git independientes, ambos fuera de `PaseoYA-Core/`. Backend contiene migraciones, RLS, configuración y operaciones confiables de Supabase; no equivale necesariamente a un servidor Node. **Estado:** carpetas/repositorios aún no creados ni verificados; remotos y proyecto cloud no conectados.

Propuesta de aislamiento: datos ficticios de demo, proyecto Supabase de desarrollo o entorno local según elección, variables en archivo de ejemplo sin valores, migraciones reproducibles y política explícita que impida ejecutar pruebas destructivas contra datos ajenos. No registrar `service_role`, claves, contraseñas ni URLs privadas en el Core.

Antes de conectar: confirmar propietario del proyecto Supabase, límites/cuotas, políticas RLS, acceso a Storage y quién puede correr migraciones. Lectura del Core no equivale a autorización de conexión.

Cuando se cree código, documentar aquí: versiones efectivamente observadas, instalación aprobada, rutas y remotos, comandos exactos de arranque, emulador/dispositivo, migración, seed sintético, pruebas y síntomas de fallo. Estado actual de comandos: **desconocido; no ejecutado**.
