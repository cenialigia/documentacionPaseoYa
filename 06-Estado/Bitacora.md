---
title: "Bitácora y handoff"
tags: [paseoya]
status: planificado
updated: 2026-10-02
---

# Bitácora y handoff

## 2026-10-02 · Creación de semilla

**Entrada:** petición de Usuario en esta sesión; fuentes SRC-01 y SRC-02 en [[09-Entradas/_Indice de entradas]].
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

**Entrada:** SRC-04 ZIP Stitch y SRC-05 instrucción de Usuario. **Integrador:** agente de esta sesión; una sola raíz objetivo `E:/Repositorios/Hackathon/PaseoYA/PaseoYA-Core`.

- Se preservó el ZIP intacto en `09-Entradas/Mockup Stitch/original.zip`, SHA-256 `096656AA0A36F3D1F73F90E033276EF7C4E08E0CD51F1D4FDE67D1CF1A783CBE`. Se copiaron seis capturas de vistas, logo, ocho HTML y `DESIGN.md` para consulta local. La variante Explorar 2 no tenía PNG ni contenido principal.
- Se creó [[02-Arquitectura/Mockup Stitch - vistas y ubicaciones]] con imágenes incrustadas, ubicación lógica, acciones, estados y conflictos MK-01–08. Se actualizó [[02-Arquitectura/Mapa de pantallas]] y se separó Mis pedidos (UI-06A) de Ticket (UI-06B).
- [[05-Desarrollo/Plan por fases]] ahora contiene F0 de herramientas y dos repositorios independientes, UI F1–F6, backend F7–F9 e integración F10. [[06-Estado/Tareas pendientes]] contiene 19 casillas. ADR-008 registra la separación solicitada; DEC-01/02/04–06/09–11/15–16 siguen sin resolver donde aplican.
- **Evidencia documental:** lectura de capturas y archivos; inventario y SHA-256 de origen. **Evidencia estática PASS (2026-10-02):** primera comprobación de 15 notas afectadas con front matter; comprobación ampliada de 27 notas del Core con 0 enlaces wiki rotos; ZIP copiado con hash idéntico al original; 7 PNG (6 vistas + logo), 8 HTML, 19 casillas y 12 pruebas planificadas. Límite: la comprobación estática no renderiza Obsidian ni ejecuta app/servicio. **Runtime:** T-F0/T-UI/T-RLS/T-STOCK y demás `NO_EJECUTADA`; no existen app, backend ni proyecto Supabase creados en esta sesión. Renderizado en Obsidian: `NO_EJECUTADA`.
- **Próximo paso:** Usuario revisa mockup, decide alcance visual/DEC-11 y opciones F0/DEC-01/02 al iniciar implementación. El siguiente agente lee Core → contexto activo → RF/RN/DEC del lote → artefacto actual; inicia F0-01 o LUI-01 y registra evidencia real.
- **Uso de sesión:** `SessionUsage/v1`: planificación/documentación `null`, inspección de mockup `null`, validación `null`; telemetría de tokens no disponible, no se declara cero.

## 2026-10-02 · Revisión del alcance «100 %»

**Entrada:** SRC-06, pregunta de Usuario sobre cobertura, pendientes y fases iniciables. **Estado:** sólo documentación; no se ejecutaron F0–F13.

- Se distinguieron tres metas en [[Decisiones de Usuario para el desarrollo]]: A demo MVP (F0–F10), B RF-01–44 completos (añade F11) y C piloto/uso real (añade F12–F13). DEC-19 queda `PENDIENTE`; no se llama «100 %» a la demo.
- Se añadieron ocho lotes condicionales COMP-01–04, OPS-01/02 y PIL-01/02 para cubrir gestión comercial/admin, extras aprobados, trazabilidad RF, distribución, seguridad/operación y aceptación real. [[06-Estado/Tareas pendientes]] tiene ahora 19 casillas de demo + 4 de B + 4 de C; [[05-Desarrollo/Testing]] añade T-FULL/T-OPS/T-PIL.
- El formulario reúne las decisiones conocidas DEC-01–16 y DEC-18–25; DEC-17 permanece resuelta. En el plan se renombraron lotes de interfaz `LUI-*` para distinguirlos de pantallas `UI-*`.
- Inicio independiente de respuestas: F0-01 inventario sin instalación y F1/LUI-01 con propuestas y datos sintéticos; F1 se cierra tras DEC-11. F0-02/03 y código esperan las decisiones indicadas. La preparación documental de pruebas también puede avanzar.
- **Pruebas estáticas PASS (2026-10-02):** 28 notas revisadas, 0 enlaces wiki rotos; 27 casillas (19 demo + 4 B + 4 C), 15 pruebas planificadas y todos los DEC-01–16/18–25 presentes en el formulario. Límite: comprobación de archivos, no de renderizado ni comportamiento. Todas las pruebas de código, servicio, dispositivo y piloto `NO_EJECUTADA`. Uso de sesión `SessionUsage/v1`: análisis `null`, documentación `null`, validación `null` por ausencia de telemetría.

## 2026-10-02 · Publicación del baúl en GitHub

**Entrada:** SRC-07, autorización expresa de Usuario. **Destino:** repositorio público `cenialigia/documentacionPaseoYa`, rama `main`.

- Se inicializó Git dentro de `PaseoYA-Core`; la raíz `PaseoYA`, `AGENTS.md` y `CLAUDE.md` quedaron fuera. Se conservaron los 54 archivos del baúl, incluidos `.obsidian`, entradas originales, mockup y el cambio reciente del propietario.
- Importación inicial: commit `7989005406c1d765aee741a33f49336a75330afa`. Antes del commit, los 54 blobs staged coincidían byte por byte con los archivos locales. Se mantuvieron finales de línea y espacios de las fuentes originales.
- `git push` creó `origin/main`; `git ls-remote` devolvió el mismo hash del commit inicial y GitHub mostró el repositorio no vacío con rama principal `main`. Este registro documental se añade en un commit posterior.
- **Límite:** esto verifica publicación de archivos, no funcionamiento de Obsidian ni de la futura app. Pruebas runtime del producto: `NO_EJECUTADA`.

## 2026-10-02 · Fase 0: F0-01 y F0-02

**Entrada:** petición actual en la sesión de Claude Code, equipo `Ferfloo27`. **Raíz:** `C:/Users/Ferfloo27/Desktop/PaseoYa`, equivalente a la raíz `E:/…/PaseoYA` del equipo de Usuario (sin unidad E: aquí). `AGENTS.md` no está disponible en este equipo y no se leyó. **Estado:** preparación del entorno; producto no implementado.

- **F0-01 PASS (EVID-F0-01):** inventario sin instalar nada, contrastado con la documentación oficial vigente de React Native 0.87, Expo SDK 57 y Supabase CLI. Node 24.19.0 cumple los tres. Android listo. Faltan Supabase CLI y el daemon de Docker. iOS sólo es posible vía Expo Go o build en la nube. Detalle en [[05-Desarrollo/Entorno local]].
- **F0-02 PASS (EVID-F0-02):** `frontend/` y `backend/` son repositorios independientes con remotos propios del propietario, y el Core `documentacion/` es un tercer repositorio. La raíz no es repositorio. No se creó ni se publicó nada.
- Se respetaron los cambios locales sin confirmar de `.obsidian/*` y el fin de línea de las decisiones de Usuario; no se confirmaron ni se revirtieron.
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
- **Próximo paso:** Usuario responde DEC-11 (y DEC-15 para imágenes). Con eso se cierra LUI-01 y arranca LUI-02 (shell de cuatro pestañas, tema y componentes con fixtures) en `frontend/`.
- **Uso de sesión:** `SessionUsage/v1`: análisis `null`, redacción `null`.

## 2026-10-03 · DEC-11/15 resueltas, LUI-01 cerrada y LUI-02 implementada

**Entrada:** respuestas de Usuario en el chat:
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

## 2026-10-03 · Decisiones del propietario y demo completa (plan de recorte)

**Entrada:** el usuario pidió responder las decisiones para avanzar. Tres tandas en el chat resolvieron DEC-03/04/05/06/07/08/09/10/16/19/20 (ADR-011). DEC-03: **entrega en menos de 1 día, 2 personas**. Se aprobó el plan «app simulada + backend aparte».

- **Frontend `c0040b1` + `c703e41`:**
  - Ajustes por decisiones: pestaña Buscar (DEC-09); sin avisos ni otras acciones extra (DEC-20); perfil con «Reportar problema»; QR de pago «SIMULADO · sin valor» con «Simular pago» (DEC-04); cancelación en Confirmado (DEC-08); ticket con QR + PIN y «Guardar ticket» (DEC-16, con `react-native-qrcode-svg`, `react-native-svg`, `react-native-view-shot` y `expo-sharing` instalados con `expo install`).
  - Login simulado por rol con áreas protegidas (DEC-10), panel de comercio y vista de admin.
  - Plazo del carrito desde la última modificación (DEC-06).
- **Defectos hallados al probar y corregidos:**
  - El aviso de «Retiro validado» se perdía porque la tarjeta cambiaba de lista y se desmontaba; ahora vive en el panel.
  - El botón flotante de Expo Go tapaba «Perfil»; se anotó en el README (sólo afecta a Expo Go).
- **Backend `2475598`:** migración con tablas, RLS por rol y `comercio_id`, y funciones SECURITY DEFINER para todas las escrituras de pedidos. Seed con catálogo y cuentas ficticias; pruebas SQL y de concurrencia.
- **Evidencia:** EVID-DEMO-a, EVID-BE-a (17/17), EVID-BE-b y EVID-BE-c en PASS. Progreso 9/19 (47,4 %).
- **Límites:** la app no usa el backend (INT-01 fuera del plazo). Sin probar en el dispositivo: «Guardar ticket» y el registro. TalkBack sigue pendiente.
- **Próximo paso:** ensayar la demo con el guion del README del frontend; después de la entrega, INT-01.
- **Uso de sesión:** `SessionUsage/v1`: decisiones `null`, implementación `null`, pruebas `null`, documentación `null`.

## 2026-10-03 · INT-01: app conectada a Supabase, con un lote paralelo de backend

**Entrada:** el usuario pidió conectar la app al backend y hacer dos tareas a la vez si era lógico.

- **Orquestación:** dos escritores en superficies sin solape. Un agente trabajó sólo en `backend/` (Realtime + pg_cron); el integrador, en `frontend/` y el Core. El integrador revisó el commit del agente antes de aceptarlo.
- **Backend `45b0e3e` (agente):** `pedidos` en la publicación `supabase_realtime` y job `expirar-pedidos` cada minuto con pg_cron 1.6.4; 17/17 PASS. **El push falló por red** y el control de permisos bloqueó el reintento del agente. No se publicó en su nombre: queda pendiente de que el usuario lo confirme.
- **Frontend `146c16a`:**
  - Datos: `@supabase/supabase-js` + `expo-sqlite` (sesión en localStorage, según la guía de Expo SDK 57); `src/lib/supabase.ts`; `src/data/modelo.ts` y `src/data/catalogo.tsx` sustituyen a los fixtures, que se borraron.
  - Sesión y pedidos: `AuthProvider` con Supabase Auth y el rol leído de `perfiles`; `OrdersProvider` con lecturas bajo RLS, todas las escrituras por RPC y refresco por Realtime.
  - Comportamiento: catálogo, carrito y pedidos se remontan por usuario; las áreas por rol muestran carga y error con reintento; se retiró el simulador de fallos del checkout. `.env` con la URL `10.0.2.2:54321` y la clave publishable, fuera de git.
- **Hallazgos al integrar:**
  - Un Metro antiguo seguía sirviendo código viejo y sin `.env`; se reinició y el log confirmó «env: load .env».
  - La regla del React Compiler contra `setState` en efectos obligó a separar la lectura pura del `setState` dentro de `.then()`.
- **Evidencia:** EVID-INT-01a y EVID-BE-d en PASS. Progreso 11/19 (57,9 %).
- **Próximo paso:** publicar el backend tras la confirmación del usuario; INT-02 en un teléfono físico.
- **Uso de sesión:** `SessionUsage/v1`: integración `null`, agente de backend 62 177 tokens (informado por el runtime), pruebas `null`, documentación `null`.

## 2026-10-03 · Backend publicado e INT-02 (teléfono físico)

**Entrada:** el usuario autorizó publicar el backend y pidió continuar con INT-02.

- **Backend `45b0e3e`** publicado (hash remoto igual al local), con confirmación expresa del usuario.
- **Conexión de dispositivos:** había un Xiaomi M2102J20SG (Android 12) conectado por USB, sin Expo Go. El usuario eligió instalarlo él mismo. Se adoptó `EXPO_PUBLIC_SUPABASE_URL=http://127.0.0.1:54321` con `adb reverse` para 8081 y 54321 en cada dispositivo: la misma configuración sirve en el emulador y en el teléfono, y no depende del Wi-Fi.
- **Pruebas en el emulador (EVID-INT-02a PASS):** Realtime con RLS, expiración por pg_cron reflejada en la app, registro de cliente con rol `CLIENTE` y «Guardar ticket».
- **Prueba en dos dispositivos (EVID-INT-02b PASS):** MIUI bloquea los toques inyectados (`INJECT_EVENTS`), así que el usuario operó el teléfono como cliente mientras el agente operaba el comercio en el emulador. Estados y ticket se sincronizaron en tiempo real en ambos sentidos. No se activó ningún ajuste de seguridad del teléfono ni se guardaron capturas suyas.
- **Documentación:**
  - [[07-Manuales/Manual de usuario]] reescrito y verificado contra la app.
  - [[08-Produccion/_Indice de produccion]] con el estado de los entregables.
  - README del frontend (`2a5a32a`) con la configuración USB y un guion de demo para dos dispositivos.
- **Tareas:** LUI-06 cerrada; INT-02 abierta sólo por la presentación. Progreso 12/19 (63,2 %).
- **Próximo paso:** la presentación del hackathon y el ensayo del guion.
- **Uso de sesión:** `SessionUsage/v1`: pruebas `null`, documentación `null`.

## 2026-10-03 · Carrito persistente (mejora de LUI-04)

**Entrada:** el usuario pidió la tarea 5 («carrito persistente») como funcionalidad acoplable a los cambios de vistas que traerá al Core.

- **Frontend `9068cd4`:** `src/state/cart-storage.ts` guarda los carritos en `localStorage` (expo-sqlite) con la clave `paseoya:carritos:v1:<usuario>` y descarta datos dañados. `CartProvider` los restaura al montarse (ya se monta por usuario) y oculta líneas de productos retirados del catálogo. Sin cambios de pantallas.
- El id del carrito no cambia, así que la clave idempotente del checkout (`chk-<carritoId>`) sigue protegiendo contra duplicados tras reiniciar la app.
- **Evidencia:** EVID-CART-a PASS.
- **Nota:** el usuario actualizará este Core con vistas nuevas; esta entrada sólo se añade al final para no generar conflictos.
- **Uso de sesión:** `SessionUsage/v1`: implementación `null`, pruebas `null`.

## 2026-10-03 · LUI-08: catálogo del comercio

**Entrada:** el usuario pidió la tarea 2 (catálogo del comercio, RF-27–31).

- **Frontend `cf9c9da`:** `src/data/catalogo-comercio.ts` lee y escribe `productos` bajo RLS (cada comercio sólo los suyos, incluidos los inactivos). Pantallas `(comercio)/catalogo` (filtros todos, activos, inactivos y sin stock; activar o desactivar) y `(comercio)/editar-producto/[productoId]` (crear o editar nombre, precio, precio anterior y stock, con validación en el cliente y en el servidor mediante CHECK). Acceso desde el panel.
- **Concurrencia:** el stock se guarda con `UPDATE … WHERE stock = <valor leído>`. Si una venta lo cambió entre medias, se avisa, se recarga y no se pisa (RN-09).
- **Defecto global corregido:** el `ScrollView` de `Screen` no persistía los toques con el teclado abierto, así que el primer toque en un botón sólo cerraba el teclado. Ahora usa `keyboardShouldPersistTaps="handled"`, lo que afecta a todos los formularios.
- **Evidencia:** EVID-LUI-08a PASS. LUI-08 queda cerrada: cola, preparación, efectivo y PIN ya estaban probados (EVID-DEMO-a, EVID-INT-02b). Progreso 13/19.
- Los datos de la base local quedaron modificados por la prueba; `npm run db:reset` restaura el seed antes de la demo.
- **Uso de sesión:** `SessionUsage/v1`: implementación `null`, pruebas `null`.

## 2026-10-03 · F14 documental por vistas de Cliente, Comercio y Administrador

**Entrada:** Usuario pidió revisar avances y cambios antes de agregar una nueva fase desde tres PDF y tres mosaicos, distinguir tareas existentes para supervisión de tareas nuevas, recortar cada cuadro y exigir decisiones antes de comenzar.

- **Contexto revisado:** 13/19 lotes de demo cerrados en el Core; EVID-INT-01/02, EVID-BE-a/b/c/d, EVID-CART-a y EVID-LUI-08a. Los repositorios de código se trabajaron en otro equipo; aquí sólo está el Core, así que su estado actual requiere inventario F14-00 y ninguna captura se declaró prueba de implementación.
- **Fuentes:** SRC-08–10 PDF Cliente (13 pp.), Comercio (31 pp.) y Administrador (10 pp.); SRC-11–13 tres mosaicos. Originales conservados sin cambios y SHA-256 en [[09-Entradas/_Indice de entradas]]. Las instrucciones internas a Claude se trataron como material de propuesta, no como órdenes operativas.
- **Salida:** 54 recortes exactos (26/14/14) incrustados por rol con ubicación y tarea `SUP`, `DELTA` o `NEW` en [[02-Arquitectura/F14 - Mapa de vistas por rol]]. [[05-Desarrollo/F14 - Revision y ampliacion por roles]] contiene puerta F14-00, lotes UI/backend/QA y criterios; [[02-Arquitectura/Decisiones F14 antes de iniciar]] contiene 14 decisiones candidatas para preguntar al arrancar. Se corrigieron portadas/progreso desactualizados.
- **Contradicciones visibles:** navbar cliente (actual/PDF/mosaico), campana/favoritos/promociones versus DEC-20, QR de pago aparente versus DEC-04, ticket antes de listo versus DEC-16, CTA admin «Marcar listo» versus PDF de supervisión y flujo comercio «Entregado» sin validación. Mantener decisiones vigentes hasta respuesta de Usuario.
- **Prueba:** `EVID-F14-DOC` PASS: 54 PNG (26/14/14), seis originales con hashes preservados, 54 tareas/embeds únicos, ningún enlace nuevo faltante y `git diff --check` sin errores. **F14 implementación/supervisión: NO_EJECUTADA**.
- **Próxima acción:** al iniciar F14, revisar commits reales de frontend/backend, generar preguntas actualizadas y solicitar respuestas por lote; después supervisar/implementar y probar según el plan. Uso de sesión: `null`.

## 2026-10-03 · Handoff de F14 y publicación del baúl

**Entrada:** Usuario pidió que, al asignar la nueva fase, se comprueben conjuntamente los cambios de los tres repositorios con el agente responsable, y autorizó commit y push de todo el baúl a `main`.

- **Plan actualizado:** F14-00.0 obliga a cotejar rama, commits locales/remotos, estado y diff de Core, frontend y backend; documentar hallazgos y acordar la base antes de supervisar o implementar tareas.
- **Alcance de publicación:** únicamente `PaseoYA-Core`, preservando los originales y 54 recortes de SRC-08–13. No se modifican ni publican frontend/backend en este handoff.
- **Estado de F14:** NO_EJECUTADA. La comprobación conjunta con el futuro agente se realiza cuando se le asigne la fase; esta entrada deja preparado el criterio.

## 2026-10-03 · Referencia impersonal al propietario

**Entrada:** el propietario pidió reemplazar su nombre por «Usuario» en los archivos del baúl y publicar el cambio en `main`.

- **Cambio:** 69 menciones sustituidas en 21 notas Markdown. Se conservaron los PDF, mosaicos y ZIP originales sin edición para mantener su procedencia y hashes.
- **Verificación:** búsqueda sin coincidencias del nombre anterior en los textos del baúl; `git diff --check` sin errores. El código de frontend/backend queda fuera del alcance de este commit.

## 2026-10-03 · F14-00: comprobación conjunta y decisiones del propietario

**Entrada:** el usuario pidió revisar que los repositorios estuvieran actualizados, leer F14 y traer las preguntas.

- **F14-00.0 · Comprobación conjunta:** `git fetch` en los tres repositorios.
  - El Core iba 2 commits por detrás (`13af925` «Documentar F14 por roles y puerta de revisión conjunta», `beb261f` «Usar Usuario en referencias del baúl»). Se integró con `git pull --ff-only`, sin conflicto. Se conservaron los 4 cambios locales de `.obsidian/`, que los commits entrantes no tocaban.
  - Frontend `cf9c9da` y backend `45b0e3e` estaban iguales a `origin/main` y sin cambios locales.
  - **Base de F14:** Core `beb261f`, frontend `cf9c9da`, backend `45b0e3e`. No había diferencias ajenas sin revisar.
- **F14-00.1 · Lista de preguntas:** se leyeron el plan F14, el mapa de vistas, los tres archivos por rol y el formulario DEC-F14-01–14, contrastados con el código. Del código surgieron DEC-F14-15 (categorías como texto suelto) y DEC-F14-16 (sin almacenamiento de imágenes).
- **F14-00.2 · Respuestas:** en cinco tandas, registradas en [[02-Arquitectura/Decisiones F14 antes de iniciar]] y en ADR-012. Lo más relevante:
  - Orden Cliente → Comercio → Admin.
  - Barras del PDF; QR simulado con pantalla propia.
  - DEC-16 se mantiene.
  - Favoritos y notificaciones; registro con datos del PDF.
  - Promociones % con aprobación.
  - Tuteo y datos de los mosaicos (sustituye parte de DEC-11).
  - Cámara + PIN; entrega en dos pasos; tabla de categorías; Storage.
- **Pendiente antes de construir:** F14-00.3 (inventario versionado de lo existente por tarea `SUP`); DEC-24 (retención de datos personales) sigue abierta.
- **Próximo paso:** F14-00.3 y luego el lote F14-UI-C (Cliente) con su F14-BE asociado, por partes y con evidencia.
- **Uso de sesión:** `SessionUsage/v1`: lectura `null`, preguntas `null`, documentación `null`.

## 2026-10-03 · F14 lote Cliente (F14-UI-C + F14-BE)

- **Agente:** Claude (Code). **Base:** frontend `cf9c9da`, backend `45b0e3e`, Core `b0c8625` ([[05-Desarrollo/F14 - Inventario base]]).
- **Backend** (`8416682`, `d5d6cf1`): migración F14 cliente (perfil ampliado, categorías, promociones con aprobación, favoritos, notificaciones, Storage, contacto del cliente) y formato es-BO en notificaciones; 25/25 pruebas SQL (EVID-F14-BE-a).
- **Frontend** (`de08a02`): vistas cliente del PDF con tuteo, pestañas Inicio/Mis pedidos/Promociones/Perfil, QR de pago con vencimiento, recuperación por código; recorrido completo en emulador (EVID-F14-CLI-a).
- **Corregido durante la prueba:** aviso del ticket antes de «listo», etiqueta de pago de pedido cancelado, monto con punto decimal en notificaciones.
- **Pendiente:** eliminar foto y galería (X-04); lote Comercio (verificar/confirmar entrega, escáner con cámara, promociones, ventas) y luego Admin; DEC-24.

## 2026-10-04 · F14 lote Comercio

- **Agente:** Claude (Code). **Base:** frontend `de08a02`, backend `d5d6cf1`.
- **Backend** (`3fcd670`): retiro en dos pasos `verificar_retiro` + `confirmar_entrega` (QR o PIN, DEC-F14-14), edición limitada del local (DEC-F14-07), `horario`, avisos del comercio; 28/28 pruebas (EVID-F14-BE-b).
- **Frontend** (`bbdece0`): barra Inicio · Pedidos · Productos · Ventas, avisos y perfil en el encabezado, detalle de pedido, «Gestionar retiro» con `expo-camera` (instalado por DEC-F14-13) o PIN, productos con foto/descripción/promociones/eliminación condicionada, ventas, perfil y edición del local; recorrido en emulador (EVID-F14-COM-a).
- **Pendiente:** leer un QR real con la cámara en el teléfono físico (lo hace una persona; MIUI bloquea toques inyectados); lote Admin (aprobar promociones, gestionar comercios/usuarios/categorías); DEC-24.

## 2026-10-04 · Rama `development` para la demo (MVP local)

- A pedido del usuario se avanzó `development` hasta `main` (fast-forward, sólo tenía el README inicial): frontend `bbdece0`, backend `3fcd670`.
- Alcance: MVP de demostración **local** (Supabase en Docker + Expo Go). Sin build instalable (APK) ni proyecto Supabase en la nube; el lote Admin de F14 y la lectura de QR con cámara en teléfono siguen pendientes.
