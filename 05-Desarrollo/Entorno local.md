---
title: "Entorno local previsto"
tags: [paseoya]
status: planificado
updated: 2026-10-03
---

# Entorno local previsto

Al crear la semilla no existían proyectos React Native/Supabase en esta raíz. Después F0 se cerró en otro equipo y la app se integró con Supabase local según [[05-Desarrollo/Testing]]. **En este workspace de Usuario sólo se observó el Core**; las rutas y versiones de código citadas abajo describen el equipo `Ferfloo27` y deben volver a comprobarse en F14-00 antes de ejecutar trabajo nuevo. Ver [[05-Desarrollo/Plan por fases]].

Topología operativa solicitada: `PaseoYA-frontend/` y `PaseoYA-backend/` como repositorios Git independientes, ambos fuera de `PaseoYA-Core/`. Backend contiene migraciones, RLS, configuración y operaciones confiables de Supabase; no equivale necesariamente a un servidor Node. **Estado (2026-10-02, F0-02):** repositorios verificados, ver tabla siguiente; proyecto Supabase cloud no conectado.

## Raíces observadas en el equipo de desarrollo actual

El Core declara la raíz `E:/Repositorios/Hackathon/PaseoYA` del equipo de Usuario. En el equipo Windows `Ferfloo27` (sin unidad E:) la raíz equivalente es `C:/Users/Ferfloo27/Desktop/PaseoYa`; no se copian rutas absolutas entre equipos. `AGENTS.md` y `CLAUDE.md` viven en la raíz del equipo de Usuario y no forman parte de ningún repositorio: aquí no están disponibles.

| Superficie | Carpeta local | Remoto `origin` | Commit observado |
| --- | --- | --- | --- |
| Core | `documentacion/` | `github.com/cenialigia/documentacionPaseoYa` | `2246b15` |
| Frontend | `frontend/` (nombre lógico `PaseoYA-frontend`) | `github.com/cenialigia/PaseoYaFrontend` | `a906e7b` (sólo README) |
| Backend | `backend/` (nombre lógico `PaseoYA-backend`) | `github.com/cenialigia/PaseoYaBackend` | `6ff801e` (sólo README) |

Cada carpeta es un repositorio independiente (`git rev-parse --show-toplevel` devuelve su propia ruta) y la raíz `PaseoYa/` no es repositorio, así que el Core no queda dentro del código. Los remotos ya existían: los creó el propietario y la sesión sólo los clonó.

## F0-01 · Herramientas observadas y compatibilidad

Comprobado el 2026-10-02 sin instalar nada. Referencias oficiales consultadas ese día: entorno React Native 0.87 (Windows/Android), Expo SDK 57 y Supabase CLI.

| Herramienta | Observado | Requisito oficial vigente | Estado |
| --- | --- | --- | --- |
| Node.js | v24.19.0 vía fnm 1.37.0 (también 18/20 instaladas) | RN 0.87 ≥ 22.11; Expo SDK 57 ≥ 22.13; Supabase CLI vía npx ≥ 20 | OK |
| Gestor | npm 12.0.2, corepack 0.35.0; yarn/pnpm/bun ausentes | npm basta | OK |
| Git | 2.41.0.windows.3 | — | OK |
| JDK | `JAVA_HOME` = JDK 17.0.8; `java` del PATH = 21.0.9 | RN recomienda JDK 17 | OK con riesgo: Gradle usa `JAVA_HOME`, pero una herramienta que use el PATH tomará la 21 |
| Android SDK | `ANDROID_HOME` definido; plataformas 30–37.0 (incluye 35), build-tools 33.0.1/34.0.0/36.0.0, cmdline-tools latest, NDK 26.1/26.3, CMake 3.22.1 | Plataforma 35, build-tools 36.0.0, cmdline-tools | OK. La versión de NDK que pida la plantilla se confirma en F0-03 |
| Emulador | 36.5.11.0; AVD `AndroidMasterEmulator`, `Pixel_10_Pro`, `Pixel_3a_API_34…`, `reactEmulator`; `emulator`/`sdkmanager` fuera del PATH | — | OK; ningún dispositivo conectado durante la comprobación |
| iOS | Windows: sin Xcode | El build iOS local requiere macOS | Sólo vía Expo Go en iPhone físico o build en la nube (EAS) |
| Docker | Docker Desktop 29.4.0, WSL 2; **daemon sin responder** | `supabase start` requiere un runtime de contenedores activo | OK cuando Docker Desktop está abierto. En Windows, `[analytics] enabled = false` en `config.toml`, porque Vector no lee el socket de Docker |
| Supabase CLI | ausente; scoop/choco ausentes | Windows: scoop o dependencia npm del proyecto (`npx supabase`); no admite instalación global por npm | Instalada como dependencia de desarrollo de `backend/`: v2.119.0 (F0-03) |
| Expo CLI / EAS | ausentes globalmente | Expo se usa con `npx`, sin instalación global | Sin bloqueo |
| Watchman | ausente | Opcional en Windows | Sin bloqueo |

**Nota histórica:** esos faltantes fueron resueltos para el entorno local de F0-03; la tabla anterior conserva los resultados del inventario inicial. El proyecto Supabase cloud sigue sin conectarse. No se necesita un servidor Node adicional por inferencia.

Propuesta de aislamiento: datos ficticios de demo, proyecto Supabase de desarrollo o entorno local según elección, variables en archivo de ejemplo sin valores, migraciones reproducibles y política explícita que impida ejecutar pruebas destructivas contra datos ajenos. No registrar `service_role`, claves, contraseñas ni URLs privadas en el Core.

Antes de conectar: confirmar propietario del proyecto Supabase, límites/cuotas, políticas RLS, acceso a Storage y quién puede correr migraciones. Lectura del Core no equivale a autorización de conexión.

Cuando se cree código, documentar aquí: versiones efectivamente observadas, instalación aprobada, rutas y remotos, comandos exactos de arranque, emulador/dispositivo, migración, seed sintético, pruebas y síntomas de fallo. Arranque (F0-03): en `frontend/`, `npm install`, `cp .env.example .env` y `npm run android`; en `backend/`, `npm install` y `npm run db:start` / `db:status` / `db:reset` / `db:stop`, con Docker Desktop abierto. El `.env` del frontend toma la URL y la clave *anon* locales de `db:status`; nunca la `service_role`.

Estado posterior: F0-01/02/03, arranque, migración y seed locales registrados en EVID-F0-01–03e; integración/pruebas en EVID-INT-01/02. Se refiere al equipo y commits indicados en [[05-Desarrollo/Testing]], no a una nueva verificación en este workspace.

Comandos de inventario reproducibles (Git Bash): `node -v`, `npm -v`, `fnm list`, `java -version`, `echo $JAVA_HOME $ANDROID_HOME`, `ls $ANDROID_HOME/{platforms,build-tools,ndk}`, `$ANDROID_HOME/emulator/emulator -list-avds`, `adb devices`, `docker info`, `command -v supabase scoop`, `git -C <repo> rev-parse --show-toplevel`.
