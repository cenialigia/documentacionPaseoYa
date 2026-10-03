---
title: "Plan de pruebas y evidencia"
tags: [paseoya]
status: planificado
updated: 2026-10-02
---

# Plan de pruebas y evidencia

Pruebas diseñadas; **T-F0 PASS** (2026-10-02, EVID-F0-01 a 03e); el resto sin ejecutar. Fuentes: PDF §§5–9 y MD RF-01–44/RN-01–09. Datos ficticios; separar cuentas cliente, comercio A, comercio B y admin.

| ID | Caso y resultado esperado | Requisito/fase |
| --- | --- | --- |
| T-F0 | `node`/gestor/toolchain/Supabase CLI observados con versiones; dos raíces Git independientes; arranque y migración local si aplica. | F0, DEC-01/02 |
| T-CAT | Búsqueda/categoría muestra comercio, precio, stock y ubicación; agotado claro. | RF-05–12, UI F3/BE F7 |
| T-RLS | Cliente no lee otro pedido; comercio A no lee/escribe B; usuario normal no administra; intento directo API rechazado. | RNF-01–03, BE F7/F9 |
| T-CART | Dos carritos por comercio; editar cantidades; caduca uno tras 4 h sin alterar pedido ya creado. | RN-02–05, RF-13–17, UI F4/BE F8 |
| T-ORD | Checkout crea un pedido de un comercio; snapshot de precio y estados de pago/pedido separados. | RN-02/05, RF-18–23, BE F8 |
| T-CHECKOUT | QR simulado y efectivo siguen rutas diferentes; error/reintento no duplica pedido ni cobra. | RF-19–22, UI F4/BE F8 |
| T-STOCK | Dos compras concurrentes con una unidad: una se acepta, otra se rechaza; stock nunca negativo, sin doble liberación. | RN-09, RNF-04/05, BE F8 |
| T-CAN | Cancelación antes de preparación, reembolso simulado y stock revertido una vez; tarde se rechaza. | RN-08, RF-25, BE F9 |
| T-RET | Código inválido/ajeno/usado/expirado se rechaza; comercio dueño valida una vez y marca entregado. | RN-01, RF-22/36/37, BE F9 |
| T-EXP | Reloj controlado o simulación de tiempo demuestra 4 h, 3 d y 14 d según DEC-06; proceso funciona sin app abierta y se puede reejecutar sin doble efecto. | RN-04/06/07, RF-17/26, BE F9 |
| T-UI | Navegación móvil con lector de pantalla/tamaños táctiles, errores/offline/vacíos; comparar capturas con diseño aprobado y verificar ubicaciones/acciones UI-01–06B y UI-07–10. | RNF-07/09, UI F1–F6 |
| T-DEMO | Recorrido end-to-end en dispositivo/entorno anunciado; presentación, código y arquitectura disponibles. | PDF §9, F10 |
| T-FULL | Matriz RF-01–44/RN/RNF con prueba y evidencia por cada RF; CRUD comercio, ventas, admin, estadísticas, promociones y extras aprobados sin rutas muertas. | F11, DEC-12/13/20–22 |
| T-OPS | Build/distribución del destino, control de acceso, carga, accesibilidad, respaldo/restauración, migración/reversa, alerta e incidente ensayados. | F12, DEC-23/24 |
| T-PIL | UAT cliente/comercio/admin con datos autorizados, monitoreo del periodo acordado y aceptación o decisión de detener. | F13, DEC-25 |

Registrar `EVID-ID | fecha | versión | dispositivo/ambiente | datos sintéticos | pasos/comando | observado | PASS/FAIL/NO_EJECUTADA | límite`. Un esquema SQL que compila no prueba RLS ni la demo. Si falta entorno, escribir NO_EJECUTADA con motivo. No usar datos reales sin permiso.

## Registro de evidencia

| EVID-ID | Fecha | Versión | Ambiente | Datos | Pasos/comando | Observado | Resultado | Límite |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| EVID-F0-01 | 2026-10-02 | — | Windows 11, equipo `Ferfloo27`, Git Bash | ninguno | comandos de inventario de [[05-Desarrollo/Entorno local]] | Node 24.19.0, npm 12.0.2, JDK 17 en `JAVA_HOME`, SDK Android 35/build-tools 36.0.0, 4 AVD, Docker 29.4.0 con daemon inactivo, Supabase CLI ausente | PASS (inventario completo y contrastado con la documentación oficial) | No instala ni arranca nada; no prueba un build |
| EVID-F0-02 | 2026-10-02 | `a906e7b` / `6ff801e` / `2246b15` | mismo equipo | ninguno | `git -C <repo> rev-parse --show-toplevel`, `git remote -v`; `git status` en la raíz | tres repositorios con raíz y `origin` propios; la raíz `PaseoYa/` no es repositorio | PASS | Sólo verifica la separación local; no publica nada |
| EVID-F0-03a | 2026-10-02 | frontend `a28e8c2` | Windows, Node 24.19.0 | ninguno | `npx expo-doctor`; `npx tsc --noEmit`; `npx expo lint`; `npx expo export --platform android` | doctor 21/21; tsc y lint con salida 0 tras corregir el hook de la plantilla; bundle Hermes Android de 3.7 MB | PASS (estática y de empaquetado) | No es una ejecución en dispositivo |
| EVID-F0-03b | 2026-10-02 | frontend `a28e8c2` | emulador AVD `Pixel_3a_API_34` (Android 14) con Expo Go 57.0.9 | ninguno | arrancar el emulador; `npx expo start --android`; captura con `adb`; `adb logcat -s ReactNativeJS:E` | Metro `packager-status:running`; Expo Go instalado y en primer plano; la pantalla muestra «PaseoYA · SDK version: 57.0.0» y el inicio de la plantilla; 0 errores JS. Captura: [[06-Estado/evidencia/EVID-F0-03b-emulador.png]] | PASS (runtime en emulador) | Un primer intento fue rechazado por el usuario; se ejecutó tras su autorización. Pendiente un dispositivo físico |
| EVID-F0-03c | 2026-10-02 | backend `aa2466a` | Docker Desktop 29.4.0 | ninguno | `npm i -D supabase`; `npx supabase init`; `npx supabase start` | CLI 2.119.0 e init correctos; `start` descargó imágenes y salió con código 4 por falta de `supabase/seed.sql` (ya añadido); después Docker Desktop quedó detenido | FAIL, superado por EVID-F0-03e | — |
| EVID-F0-03e | 2026-10-02 | backend `9dce273` | Docker Desktop 29.4.0, Windows | migración temporal `f0_smoke` | `npx supabase start`; `db reset` con la migración; `psql` dentro de `supabase_db_paseoya`; retirar la migración y `db reset` | primer `start`: Vector en bucle de reinicio (no lee el socket de Docker en Windows), con Studio y edge runtime detenidos. Con `[analytics] enabled = false`, los 10 contenedores quedan arriba y Studio responde HTTP 307. Un `db reset` falló una vez con `DbSetupError` transitorio y al repetirlo funcionó: aplicó la migración y el seed, se leyó la fila `1 F0-03 smoke` y quedó registrada la versión `20261002000000`. El reset final dejó el esquema sin la tabla | PASS (runtime local) | La migración de prueba no se versionó; el esquema real es BE-01 |
| EVID-F0-03d | 2026-10-02 | `a28e8c2` / `aa2466a` | GitHub | ninguno | `git push origin HEAD`; `git ls-remote origin HEAD` | los hashes remotos coinciden con los locales en ambos repositorios | PASS | Publicación autorizada en el chat (DEC-02) |
| EVID-LUI-01a | 2026-10-03 | Core | análisis estático en Python sobre los archivos de SRC-04 | ninguno | extraer `tailwind.config` y clases de los 8 HTML; contar el uso de tokens; comparar con `DESIGN.md`; calcular el contraste WCAG | los 5 HTML con paleta coinciden con el front matter M3; la prosa de `DESIGN.md` difiere y 3 de sus colores fallan AA con texto blanco; chips de estado entre 7,23 y 7,64; `outline-variant` 1,71 no sirve para controles; recursos externos: Tailwind CDN, Google Fonts y fotos `lh3.googleusercontent.com` | PASS (documental/estática) | No sustituye a T-UI en dispositivo; LUI-01 sigue abierta hasta DEC-11 |
