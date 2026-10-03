---
title: "Bitácora y handoff"
tags: [paseoya]
status: planificado
updated: 2026-10-02
---

# Bitácora y handoff

## 2026-10-02 · Creación de semilla

**Entrada:** petición de Paulo en esta sesión; fuentes SRC-01 y SRC-02 en [[09-Entradas/_Indice de entradas]].
**Estado:** documentación propuesta; implementación no iniciada.

- Raíz objetivo: `E:/Repositorios/Hackathon/PaseoYA`. Core: `PaseoYA-Core`.
- Estructura basada en `nextjs+nestjs/Plantilla-Core-Proyecto`, adaptada a React Native + Supabase/PostgreSQL; cerebro de dominio formal **sin asignar**.
- PDF oficial: retiro presencial y entregables de hackathon; MD: 44 RF, 9 RN, 10 RNF y 7 CU, con mayor detalle de dominio.
- Bocetos V0 documentados; marca y pantallas finales no aprobadas.
- Código, Supabase, test de runtime, demo y diseño visual final: no iniciados.
- Riesgos principales: pagos simulados y vencimiento; concurrencia/stock; autorización por comercio; tiempo de hackathon desconocido.
- Siguiente paquete: P-01. Leer [[02-Arquitectura/Decisiones pendientes]] y [[05-Desarrollo/Plan por fases]].

Para relevo entre agentes: actualizar esta nota con tarea/intent/revisión, autor integrador, archivos tocados, evidencia, decisiones nuevas, bloqueo y próxima acción. No almacenar razonamiento privado ni secretos.

## 2026-10-02 · Mockup Stitch y nuevo plan UI/backend

**Entrada:** SRC-04 ZIP Stitch y SRC-05 instrucción de Paulo. **Integrador:** agente de esta sesión; una sola raíz objetivo `E:/Repositorios/Hackathon/PaseoYA/PaseoYA-Core`.

- Se preservó el ZIP intacto en `09-Entradas/Mockup Stitch/original.zip`, SHA-256 `096656AA0A36F3D1F73F90E033276EF7C4E08E0CD51F1D4FDE67D1CF1A783CBE`. Se copiaron seis capturas de vistas, logo, ocho HTML y `DESIGN.md` para consulta local. La variante Explorar 2 no tenía PNG ni contenido principal.
- Se creó [[02-Arquitectura/Mockup Stitch - vistas y ubicaciones]] con imágenes incrustadas, ubicación lógica, acciones, estados y conflictos MK-01–08. Se actualizó [[02-Arquitectura/Mapa de pantallas]] y se separó Mis pedidos (UI-06A) de Ticket (UI-06B).
- [[05-Desarrollo/Plan por fases]] ahora contiene F0 de herramientas y dos repositorios independientes, UI F1–F6, backend F7–F9 e integración F10. [[06-Estado/Tareas pendientes]] contiene 19 casillas. ADR-008 registra la separación solicitada; DEC-01/02/04–06/09–11/15–16 siguen sin resolver donde aplican.
- **Evidencia documental:** lectura de capturas y archivos; inventario y SHA-256 de origen. **Evidencia estática PASS (2026-10-02):** primera comprobación de 15 notas afectadas con front matter; comprobación ampliada de 27 notas del Core con 0 enlaces wiki rotos; ZIP copiado con hash idéntico al original; 7 PNG (6 vistas + logo), 8 HTML, 19 casillas y 12 pruebas planificadas. Límite: la comprobación estática no renderiza Obsidian ni ejecuta app/servicio. **Runtime:** T-F0/T-UI/T-RLS/T-STOCK y demás `NO_EJECUTADA`; no existen app, backend ni proyecto Supabase creados en esta sesión. Renderizado en Obsidian: `NO_EJECUTADA`.
- **Próximo paso:** Paulo revisa mockup, decide alcance visual/DEC-11 y opciones F0/DEC-01/02 al iniciar implementación. El siguiente agente lee Core → contexto activo → RF/RN/DEC del lote → artefacto actual; inicia F0-01 o LUI-01 y registra evidencia real.
- **Uso de sesión:** `SessionUsage/v1`: planificación/documentación `null`, inspección de mockup `null`, validación `null`; telemetría de tokens no disponible, no se declara cero.

## 2026-10-02 · Revisión del alcance «100 %»

**Entrada:** SRC-06, pregunta de Paulo sobre cobertura, pendientes y fases iniciables. **Estado:** sólo documentación; no se ejecutaron F0–F13.

- Se distinguieron tres metas en [[Decisiones de Usuario para el desarrollo]]: A demo MVP (F0–F10), B RF-01–44 completos (añade F11) y C piloto/uso real (añade F12–F13). DEC-19 queda `PENDIENTE`; no se llama «100 %» a la demo.
- Se añadieron ocho lotes condicionales COMP-01–04, OPS-01/02 y PIL-01/02 para cubrir gestión comercial/admin, extras aprobados, trazabilidad RF, distribución, seguridad/operación y aceptación real. [[06-Estado/Tareas pendientes]] tiene ahora 19 casillas de demo + 4 de B + 4 de C; [[05-Desarrollo/Testing]] añade T-FULL/T-OPS/T-PIL.
- El formulario reúne las decisiones conocidas DEC-01–16 y DEC-18–25; DEC-17 permanece resuelta. En el plan se renombraron lotes de interfaz `LUI-*` para distinguirlos de pantallas `UI-*`.
- Inicio independiente de respuestas: F0-01 inventario sin instalación y F1/LUI-01 con propuestas y datos sintéticos; F1 se cierra tras DEC-11. F0-02/03 y código esperan las decisiones indicadas. La preparación documental de pruebas también puede avanzar.
- **Pruebas estáticas PASS (2026-10-02):** 28 notas revisadas, 0 enlaces wiki rotos; 27 casillas (19 demo + 4 B + 4 C), 15 pruebas planificadas y todos los DEC-01–16/18–25 presentes en el formulario. Límite: comprobación de archivos, no de renderizado ni comportamiento. Todas las pruebas de código, servicio, dispositivo y piloto `NO_EJECUTADA`. Uso de sesión `SessionUsage/v1`: análisis `null`, documentación `null`, validación `null` por ausencia de telemetría.

## 2026-10-02 · Publicación del baúl en GitHub

**Entrada:** SRC-07, autorización expresa de Paulo. **Destino:** repositorio público `cenialigia/documentacionPaseoYa`, rama `main`.

- Se inicializó Git dentro de `PaseoYA-Core`; la raíz `PaseoYA`, `AGENTS.md` y `CLAUDE.md` quedaron fuera. Se conservaron los 54 archivos del baúl, incluidos `.obsidian`, entradas originales, mockup y el cambio reciente del propietario.
- Importación inicial: commit `7989005406c1d765aee741a33f49336a75330afa`. Antes del commit, los 54 blobs staged coincidían byte por byte con los archivos locales. Se mantuvieron finales de línea y espacios de las fuentes originales.
- `git push` creó `origin/main`; `git ls-remote` devolvió el mismo hash del commit inicial y GitHub mostró el repositorio no vacío con rama principal `main`. Este registro documental se añade en un commit posterior.
- **Límite:** esto verifica publicación de archivos, no funcionamiento de Obsidian ni de la futura app. Pruebas runtime del producto: `NO_EJECUTADA`.

## 2026-10-02 · Fase 0: F0-01 y F0-02

**Entrada:** petición actual en la sesión de Claude Code, equipo `Ferfloo27`. **Raíz:** `C:/Users/Ferfloo27/Desktop/PaseoYa`, equivalente a la raíz `E:/…/PaseoYA` del equipo de Paulo (sin unidad E: aquí). `AGENTS.md` no está disponible en este equipo y no se leyó. **Estado:** preparación del entorno; producto no implementado.

- **F0-01 PASS (EVID-F0-01):** inventario sin instalar nada, contrastado con la documentación oficial vigente de React Native 0.87, Expo SDK 57 y Supabase CLI. Node 24.19.0 cumple los tres. Android listo. Faltan Supabase CLI y el daemon de Docker. iOS sólo es posible vía Expo Go o build en la nube. Detalle en [[05-Desarrollo/Entorno local]].
- **F0-02 PASS (EVID-F0-02):** `frontend/` y `backend/` son repositorios independientes con remotos propios del propietario, y el Core `documentacion/` es un tercer repositorio. La raíz no es repositorio. No se creó ni se publicó nada.
- Se respetaron los cambios locales sin confirmar de `.obsidian/*` y el fin de línea de las decisiones de Paulo; no se confirmaron ni se revirtieron.
- **Orquestación:** se mantiene la evaluación vigente del plan: coordinación por archivos del Core, un solo escritor y sin runtime adicional.
- **Pendiente:** DEC-01/02 antes de F0-03; Docker Desktop activo antes de `supabase start`. EVID-F0-03 queda `NO_EJECUTADA`.
- **Uso de sesión:** `SessionUsage/v1`: lectura `null`, inventario `null`, documentación `null`; el runtime no expone telemetría de tokens.

## 2026-10-02 · Fase 0: DEC-01/02 y F0-03 parcial

**Entrada:** respuestas en el chat de la sesión: Android + Expo, Supabase local con Docker, y autorización para inicializar, instalar dependencias, hacer commit y push. Registrado en el formulario, en Decisiones pendientes y en ADR-009.

- **Frontend `a28e8c2`:** plantilla `create-expo-app` Expo SDK 57 (RN 0.86.3, React 19.2.3, Expo Router), renombrada a PaseoYA, con `.env.example` sin valores. Se omitieron la `LICENSE` de Expo (la licencia la decide el propietario) y `.claude/settings.json` (activaba un plugin sin autorización). Se corrigió el hook `use-color-scheme.web.ts` para que pase lint. EVID-F0-03a PASS.
- **Backend `aa2466a`:** Supabase CLI 2.119.0 como dependencia de desarrollo, `supabase init`, `project_id = "paseoya"`, scripts `db:*` y seed vacío. Sin proyecto cloud ni claves. `supabase start` falló (EVID-F0-03c) por falta del seed, ya corregido; después Docker Desktop quedó detenido y no se relanzó sin consultar.
- **Push** de ambos repositorios verificado (EVID-F0-03d). El Core no se confirmó ni se publicó: tiene cambios locales previos en `.obsidian/` y la autorización de push cubría sólo frontend y backend.
- El arranque del emulador fue rechazado por el usuario: EVID-F0-03b `NO_EJECUTADA`.
- **Próximo paso F0:** con Docker abierto, `npm run db:start` y `npm run db:reset` en `backend/`; luego, con autorización, la app en un emulador o dispositivo. Con ambas en PASS, F0-03 y T-F0 se cierran.
- **Uso de sesión:** `SessionUsage/v1`: decisiones `null`, bootstrap `null`, documentación `null`; sin telemetría de tokens.

## 2026-10-02 · F0-03: Supabase local verificado

**Entrada:** el usuario pidió abrir Docker y continuar con `supabase start`.

- Docker Desktop se abrió y el daemon 29.4.0 respondió. El primer `start` dejó Vector en bucle de reinicio y Studio y edge runtime detenidos, por la limitación de Windows con el socket de Docker. Se desactivó Analytics en `config.toml` (backend `9dce273`, publicado con hashes verificados) y los 10 contenedores quedaron arriba.
- Migración temporal `f0_smoke`: aplicada por `db reset` y verificada con `psql`; después se retiró y se limpió con otro reset. Un `DbSetupError` transitorio queda anotado en EVID-F0-03e. **EVID-F0-03e PASS.**
- El stack local sigue en ejecución; se detiene con `npm run db:stop`.
- **Próximo paso F0:** EVID-F0-03b, la app en un emulador o dispositivo con autorización. Con eso se cierran F0-03 y T-F0. Después: F1/LUI-01 (requiere DEC-11) o BE-01 (requiere F1 aceptada y decisiones de datos y roles).
- **Uso de sesión:** `SessionUsage/v1`: runtime `null`, documentación `null`.

## 2026-10-02 · F0 cerrada

**Entrada:** el usuario pidió hacer commit y push del Core (`bcd9295`, sin incluir los cambios locales de `.obsidian/`) y continuar con lo pendiente.

- Emulador AVD `Pixel_3a_API_34` (Android 14) arrancado; `npx expo start --android` instaló Expo Go 57.0.9 y abrió PaseoYA (SDK 57.0.0), con 0 errores JS. Captura en [[06-Estado/evidencia/EVID-F0-03b-emulador.png]]. **EVID-F0-03b PASS → F0-03 y T-F0 cerradas; F0 3/3.**
- Metro se detuvo después de la captura, al agotar el límite de tiempo de la tarea en segundo plano; se relanza con `npm run android` en `frontend/`. Quedan en ejecución el emulador y el stack de Supabase (`npm run db:stop` en `backend/`).
- **Siguiente fase:** F1/LUI-01, la especificación visual desde SRC-04. Puede avanzar con propuestas y sólo se cierra con DEC-11. La primera tanda de decisiones (DEC-19, 03, 10, 11 y 15) desbloquea F2.
- **Uso de sesión:** `SessionUsage/v1`: runtime `null`, documentación `null`.

## 2026-10-03 · F1/LUI-01: especificación UI propuesta

**Entrada:** el usuario pidió continuar tras cerrar F0. LUI-01 puede avanzar sin decisiones, pero sólo se cierra con DEC-11 (Plan por fases).

- Se creó [[02-Arquitectura/Especificacion UI LUI-01]] con: tokens canónicos (la paleta M3 de los HTML, con contraste medido), tipografía, espaciado, objetivo táctil de 48 dp, rutas Expo Router por rol, inventario de componentes, matriz vista→estado→acción, estados de pedido y pago separados, glosario y frases prohibidas, fixtures coherentes (TechZone = Local 208, que resuelve MK-06), licencias de recursos y propuestas para MK-01–08.
- **Hallazgos:**
  - Los colores de la prosa de `DESIGN.md` no coinciden con los HTML y tres fallan AA con texto blanco.
  - `outline-variant` no alcanza 3:1 para bordes de controles.
  - Las fotos de Stitch tienen licencia desconocida y no se usarán.
- Enlaces añadidos en Inicio, Contexto activo, Mapa de pantallas, la nota del mockup y DEC-11 (lista de 8 puntos para responder).
- **Evidencia:** EVID-LUI-01a PASS (documental/estática). T-UI `NO_EJECUTADA`. LUI-01 sigue abierta.
- **Próximo paso:** Paulo responde DEC-11 (y DEC-15 para imágenes). Con eso se cierra LUI-01 y arranca LUI-02 (shell de cuatro pestañas, tema y componentes con fixtures) en `frontend/`.
- **Uso de sesión:** `SessionUsage/v1`: análisis `null`, redacción `null`.

## 2026-10-03 · DEC-11/15 resueltas, LUI-01 cerrada y LUI-02 implementada

**Entrada:** respuestas de Paulo en el chat:
- DEC-11: especificación aprobada tal cual.
- Logo: texto provisional.
- DEC-15: placeholders sin marca.
- Textos y datos: TechZone en «208, planta baja» y trato formal (usted).

- Registrado en el formulario, en Decisiones pendientes, en ADR-010 y en la especificación (estado `aprobado`). **LUI-01 cerrada (EVID-LUI-01b).**
- **LUI-02, frontend `cdf4aa8`:**
  - Tokens en `src/constants/theme.ts`, Plus Jakarta Sans (`@expo-google-fonts/plus-jakarta-sans`) y `userInterfaceStyle: light`.
  - Grupo `(cliente)` con `NativeTabs` de 4 pestañas e iconos Material Symbols (prop `md`), con insignia de carritos.
  - Pila con tienda, producto, checkout, ticket, cuenta y avisos.
  - Componentes base: texto, botón con bloqueo de doble toque, chips, tarjeta, precio y estados.
  - Un único módulo de fixtures y el hook `useNow`.
  - Se retiraron los archivos de demostración de la plantilla.
- **Hallazgos al probar:**
  - La búsqueda no encontraba «Audífonos» con «audi» porque `normalize` no actúa en Hermes; se cambió a un mapa explícito.
  - Las etiquetas de pestaña requieren la prop en cada `Trigger`.
  - El watcher de Metro dejó de detectar una edición y hubo que reiniciarlo con `--clear`.
  - `expo start --android` sin dispositivo lanza otro AVD por su cuenta: es preferible arrancar Metro solo y abrir la app con un enlace `exp://`.
  - Durante la prueba se activó por error el inspector de Expo Go y unos toques cayeron en el lanzador; sin efectos.
- **Evidencia:** EVID-LUI-02a PASS en emulador. TalkBack y texto al 200 % siguen `NO_EJECUTADA`, por eso LUI-02 sigue abierta.
- **Próximo paso:** prueba de accesibilidad de LUI-02 y después LUI-03. BE-01 espera DEC-10 (roles y altas).
- **Uso de sesión:** `SessionUsage/v1`: implementación `null`, pruebas `null`, documentación `null`.

## 2026-10-03 · Accesibilidad de LUI-02 y LUI-03 implementada

**Entrada:** el usuario pidió hacer la prueba de accesibilidad en el emulador y continuar con LUI-03.

- **Auditoría de accesibilidad (EVID-LUI-02b PASS):** script que, sobre `uiautomator dump`, busca tocables sin nombre y objetivos menores de 48 dp, más capturas al 200 %. Se corrigieron dos defectos (frontend `9f31bb3`): chips de 36 dp → área de 48 dp, y chips de estado que se salían de la tarjeta → filas con salto de línea.
- **TalkBack (EVID-LUI-02c `NO_EJECUTADA`):** se activó por `settings`; su permiso de notificaciones se **denegó** (opción más conservadora). Los gestos y atajos inyectados por adb no movieron el foco y `screencap` devolvió imágenes congeladas. Se desactivó TalkBack y la escala de texto volvió a 1,0. Hace falta una pasada manual breve.
- **LUI-03, frontend `2f36838`:**
  - Estado de carritos en cliente (`src/state/cart.tsx`): un carrito por comercio que se crea si no existe; comprueba stock y comercio cerrado; no reserva stock (DEC-05); plazo ilustrativo de 4 h (DEC-06).
  - Pantallas: categorías y ofertas en Explorar; tienda real con aviso de cerrado; detalle con selector de cantidad accesible (rol `adjustable`); Comparar con resumen de menor precio y aviso de que la equivalencia no está verificada (DEC-09).
- **Evidencia:** EVID-LUI-03a PASS en emulador; el rechazo por falta de stock y el comercio cerrado quedaron verificados.
- **Nota operativa (corregida el 2026-10-03):** el problema no era un watcher inestable. Metro se arrancaba con `CI=1`, que desactiva la vigilancia de archivos y las recargas (lo dice su log). Hay que arrancarlo sin `CI`, como proceso independiente, para que no lo corte el límite de tiempo de las tareas en segundo plano.
- **Próximo paso:** LUI-04 (carritos completos). Decisiones útiles: DEC-09 para cerrar LUI-03, DEC-05/06 para el texto de carritos y DEC-10 para el backend.
- **Uso de sesión:** `SessionUsage/v1`: pruebas `null`, implementación `null`, documentación `null`.

## 2026-10-03 · LUI-04: carritos completos

**Entrada:** el usuario pidió continuar con LUI-04.

- **Frontend `9c264fd`:**
  - El estado de carritos añade cambio de cantidad, quitar línea (un carrito vacío desaparece), eliminar carrito con confirmación nativa y recuperar un vencido. Al recuperar sólo vuelven los productos con stock, la cantidad se limita al disponible, se suma a un carrito activo del mismo comercio si existe y no se permite si el comercio está cerrado.
  - La pantalla muestra el temporizador por segundo con aviso en los últimos 5 minutos (el lector anuncia minutos), los avisos de stock cambiante que bloquean el pago hasta corregirlos, la ubicación de retiro y el bloque «Cómo funciona».
  - Texto prudente: «La disponibilidad se confirma al pagar» (DEC-05).
- Fixtures ajustados para cubrir los estados: chaqueta 7 de 6 en stock y un carrito TechZone vencido con un producto agotado. Se retiró el carrito vencido de Café, que estaba cerrado.
- **Evidencia:** EVID-LUI-04a PASS en emulador.
- **Hallazgo operativo:** el modo CI de Metro explica los «fallos del watcher» anteriores; la nota anterior quedó corregida.
- **Próximo paso:** LUI-05 (checkout) con marcadores hasta DEC-04/05/06. Siguen pendientes la pasada manual con TalkBack (LUI-02), DEC-09 (LUI-03) y DEC-10 (backend).
- **Uso de sesión:** `SessionUsage/v1`: implementación `null`, pruebas `null`, documentación `null`.

## 2026-10-03 · LUI-05: checkout de un comercio

**Entrada:** el usuario pidió continuar con LUI-05.

- **Frontend `780a59c`:**
  - Estado de pedidos (`src/state/orders.tsx`) con un servicio simulado y clave de idempotencia derivada del carrito (`chk-<carritoId>`): un carrito sólo puede convertirse en un pedido. El pedido nace `CONFIRMED` con pago `PENDING`, separado del carrito (RN-05).
  - Checkout con un comercio, un local y un total de productos (sin suponer tarifas). Selector accesible (`radiogroup`) de QR de pago simulado o efectivo, bloque de retiro presencial y estados procesando, error y reintento. Doble barrera contra el doble toque: botón con `loading` y un `ref` de envío en curso.
  - Al confirmar, `router.replace` lleva al detalle del pedido, con bloques PAGO y RETIRO separados.
  - Selector de fallo de conexión sólo en `__DEV__`.
- **Marcadores:** [DEC-04] para la confirmación del pago simulado y [plazo DEC-06] para los plazos. «Total de productos» evita afirmar que no hay cargos (DEC-21).
- **Hallazgos al probar:**
  - El título del encabezado coincidía con el texto del botón y confundió al script; no era un defecto de la app.
  - La ruta índice `pedido/[pedidoId]/index` terminaba en «Unmatched Route»; se renombró a `detalle`.
  - Con React Compiler, `siguiente.current++` saltaba un número (se confirmó con un registro temporal, ya retirado); la idempotencia nunca falló.
- **Evidencia:** EVID-LUI-05a PASS (servicio simulado). La idempotencia real se probará en BE-03.
- **Próximo paso:** LUI-06, con DEC-16/20 pendientes. Las decisiones abiertas bloquean ya el cierre de LUI-02 a 05.
- **Uso de sesión:** `SessionUsage/v1`: implementación `null`, pruebas `null`, documentación `null`.
