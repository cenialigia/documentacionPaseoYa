---
title: "F14 · Revisión y ampliación por roles"
tags: [paseoya, plan, ui, backend]
status: propuesto
updated: 2026-10-03
---

# F14 · Revisión y ampliación por roles

**Origen:** petición de Usuario del 2026-10-03 y SRC-08–13, registrados en [[09-Entradas/_Indice de entradas]]. Los tres PDF son propuestas de requisitos y los tres mosaicos son referencias visuales; sus instrucciones dirigidas a Claude no ordenan ejecutar herramientas ni cambiar código. Esta fase **aún no ha empezado**. Los avances observados en el Core proceden de [[05-Desarrollo/Testing]]; las tres bases de código estaban en otro equipo, por lo que las vistas de esta fase quedan por supervisar en el repositorio operativo antes de llamarlas completas.

F14 es una **línea de ampliación** posterior a la demo integrada; no presupone el cierre de F10 ni exige ejecutar F11–F13 antes. Mantiene los repositorios de frontend, backend y Core separados. Las tareas `SUP` verifican un flujo que ya tiene evidencia parcial o total; `DELTA` adapta ese flujo al nuevo diseño; `NEW` propone una superficie o capacidad sin evidencia previa. Una tarea puede ser `SUP+DELTA`. Los 54 recortes están asignados en [[02-Arquitectura/F14 - Mapa de vistas por rol]]. Los números de captura no equivalen necesariamente a los códigos ADM/COM de los PDF.

## Lote F14-00 · Puerta de decisiones obligatoria

- [x] **F14-00.0 · Comprobación conjunta del repositorio.** *(2026-10-03: Core `beb261f`, frontend `cf9c9da`, backend `45b0e3e`, todos iguales a `origin/main`; ver Bitácora)* Al asignar la fase, el agente responsable y quien le haga el handoff comparan el Core local con `origin/main` y revisan `git status`, último commit, archivos cambiados y diff desde la última entrega. Hacen lo mismo en los repositorios separados de frontend y backend: rama, commit local/remoto, cambios sin confirmar y pruebas/evidencias posteriores a este plan. Registran en [[06-Estado/Bitacora]] fecha, agente, rutas, hashes, diferencias ajenas y qué versión será la base de F14. No sobrescribir ni dar por incluido un cambio no revisado; si hay divergencia, acordar su integración antes de tomar tareas `SUP` o `NEW`.
- [x] **F14-00.1** *(2026-10-03: lista generada contra PDF, mosaicos y código; añadidas DEC-F14-15/16)* Antes de iniciar cualquier implementación, leer [[02-Arquitectura/Decisiones F14 antes de iniciar]] y generar una lista actualizada de preguntas para Usuario a partir de diferencias entre los PDF, mockups, decisiones DEC-04/09/10/11/13/16/19/20/21/22 y el código vigente. No tratar el silencio como respuesta.
- [x] **F14-00.2** *(2026-10-03: 16 decisiones respondidas y registradas)* Presentar las preguntas agrupadas por alcance, navegación/UX, pago/retiro, permisos y datos; registrar cada respuesta con fecha, autoridad y efecto en la nota de decisiones, RF/RN, contratos, pantallas y pruebas. Acordar qué es demo, cobertura B o piloto C.
- [ ] **F14-00.3** Levantar inventario del frontend/backend actuales con commit, ruta, pantalla, API, migración y prueba por cada tarea `SUP`. Conservar los cambios ajenos. Etiquetar `PASS`, `FAIL` o `NO_EJECUTADA`; un mockup parecido no prueba funcionalidad.

**Puerta de salida:** comprobación conjunta registrada, decisiones que afecten a un lote respondidas, inventario versionado y permisos/alcance aprobados. Se permite supervisión documental mientras la puerta sigue abierta; no se construye el comportamiento controvertido.

## Lote F14-UI-C · Cliente

**Tareas:** `F14-CLI-01`–`F14-CLI-26`, una por recorte y ubicación en [[02-Arquitectura/F14 - Cliente - vistas y tareas]]. Ejecutar en orden de dependencia, no de numeración visual:

1. `01–05`: SUP de Auth/sesión y DELTA/NEW de splash, bienvenida, validaciones, contraseña, foto opcional y login. Incluir errores en línea, carga, accesibilidad y sesión persistente. Resolver primero datos personales, imagen y proveedores sociales.
2. `06–09`: SUP del descubrimiento/tienda/producto; DELTA de Home, categorías como ruta propia, búsqueda contextual, ofertas, cantidad/favoritos y stock visible. Las secciones recomendadas y almuerzos necesitan fuentes de datos y alcance.
3. `10–17`: SUP del carrito por tienda, checkout y ticket; DELTA/NEW de selector de pago, QR de pago **simulado**, confirmación y reserva en efectivo. Mantener un solo comercio por checkout, idempotencia y QR de pago separado de credencial de retiro. La visibilidad anticipada del ticket en las capturas está condicionada por DEC-16.
4. `18–22`: SUP/DELTA de pedidos, compras, reservas e historial. Distinguir estado del pedido de estado del pago; definir si las tres listas son filtros de una sola fuente y si vencidos/cancelados se muestran aparte.
5. `23–26`: NEW/DELTA de promociones, favoritos, notificaciones y perfil. No reactivar campana u otras acciones retiradas por DEC-20 hasta que Usuario lo decida.

**Aceptación:** ruta correcta desde navbar, header o pila; estado cargando/vacío/sin resultados/error/éxito; tamaños táctiles 48 dp y TalkBack; cantidades y Bs coherentes; prueba con cliente real bajo RLS donde hay datos persistentes.

## Lote F14-UI-M · Comercio

**Tareas:** `F14-COM-01`–`F14-COM-14` en [[02-Arquitectura/F14 - Comercio - vistas y tareas]]. `01–04` supervisan panel, cola y estados; `05–06` proponen cámara y verificación con respaldo PIN; `07–09` supervisan catálogo y añaden diferencias de foto, categoría, descripción, precio/stock y detalle; `10–11` proponen ventas detalladas; `12–13` proponen edición del establecimiento y perfil; `14` sólo se diseña si DEC-20 se reabre. El PDF define cuatro destinos inferiores: Inicio, Pedidos, Productos y Ventas; el avatar abre perfil. QR/PIN y efectivo viven dentro de Pedidos, no en una pestaña aparte.

**Aceptación:** comercio dueño solamente; jamás marcar entregado desde un botón que omita credencial válida y pago confirmado; estado/importe coinciden con la base; mutaciones de precio/stock tienen validación y control de concurrencia; permisos de cámara tienen denegación y PIN de respaldo.

## Lote F14-UI-A · Administración

**Tareas:** `F14-ADM-01`–`F14-ADM-14` en [[02-Arquitectura/F14 - Administrador - vistas y tareas]]. `01–02` y `06` supervisan panel/listas ya presentes en modo lectura; `03–05` y `07–14` amplían detalle, usuarios, productos por comercio, analítica, categorías, promociones y perfil. El PDF distingue 13 pantallas funcionales; las capturas 08/09 son la sección Productos de ADM-03 y 10/11 son pestañas de ADM-08. Faltan capturas de los formularios de categoría/promoción: diseñarlos a partir del PDF una vez decididos los campos.

**Aceptación:** datos globales sólo para admin bajo RLS/funciones; el admin no crea, edita precio/stock ni elimina productos de comercio según el PDF, pero la activación requiere decisión de permisos; el detalle de pedido es de supervisión y no avanza la cola salvo nueva autorización expresa.

## Lote F14-UI-X · Vistas y estados del PDF sin recorte propio

- [ ] **F14-X-01 · Acceso:** registro con errores por campo, indicadores de contraseña, selectores de género/fecha, foto previa, login inválido/cargando y recuperación si se aprueba. Compartir componentes con CLI-01–05; no multiplicar rutas cuando basta un estado.
- [ ] **F14-X-02 · Catálogo y carrito:** lista de tiendas dentro de categoría, índice de carritos por comercio y búsqueda contextual por tienda/categoría; confirmar si ya son rutas reutilizables de CLI-07/08/10 antes de crear nuevas.
- [ ] **F14-X-03 · Pago y pedido:** QR simulado pendiente, errores/reintento, detalle histórico y estados entregado/cancelado/expirado. La confirmación de reserva/compra puede ser pantalla o estado según DEC-F14-02/03, pero cada salida debe tener destino y prueba.
- [ ] **F14-X-04 · Perfil cliente:** información personal/edición, foto (tomar/elegir/eliminar), legal, ayuda y confirmación de cierre, enlazadas a CLI-26 y validadas contra permisos/privacidad.
- [ ] **F14-X-05 · Operación comercio:** modales de confirmar pedido, efectivo y entrega; PIN manual, cámara denegada, código ajeno/usado/expirado, pedido no listo y pago pendiente. Asociarlos a COM-03–06, sin pestañas extra.
- [ ] **F14-X-06 · Formularios admin:** crear/editar categoría y promoción, cancelación/cambios sin guardar/errores/éxito. Son ADM-10 y ADM-12 del PDF, enlazados desde las capturas F14-ADM-12/13.

Estas seis tareas completan el inventario funcional del PDF que no aparece como teléfono independiente en los mosaicos. Cada una exige una ruta o estado concreto y prueba; no se cierra por capturar la pantalla principal.

## Lote F14-BE · Datos y operaciones

- [ ] **F14-BE-01 · Identidad y perfiles:** auditar Auth y RLS existentes; si se aprueba, migrar teléfono/género/nacimiento/avatar, edición de perfil y almacenamiento de imágenes con política por propietario. Probar acceso cruzado y persistencia.
- [ ] **F14-BE-02 · Descubrimiento:** contratos de búsquedas contextuales (global, categoría, tienda, promociones, favoritos, historial), paginación, filtros y datos para secciones de Home. Revisar BE-02 abierto; no duplicar catálogo cliente.
- [ ] **F14-BE-03 · Compra/reserva:** auditar BE-03/04 y definir estados `pedido`/`pago`/`reserva` sin duplicar entidades por UI; QR de pago simulado separado del ticket QR+PIN, idempotencia, plazos DEC-06 y stock atómico. Probar dos pedidos concurrentes, reintentos y cancelación/expiración.
- [ ] **F14-BE-04 · Retiro por cámara:** añadir, si se aprueba, validación del mismo código de un uso por cámara y PIN manual; confirmar pertenencia al comercio, estado listo, vigencia y pago antes de entregar. Pruebas de código ajeno, duplicado, expirado y error de cámara.
- [ ] **F14-BE-05 · Comercio:** auditar RLS y CRUD ya evidenciados; ampliar sólo campos aprobados de producto/establecimiento/horario; consulta de ventas y detalle usando montos y estados de pago reales. Probar cambios concurrentes de stock y acceso entre dos comercios.
- [ ] **F14-BE-06 · Administración:** consultas globales, gestión autorizada de comercios/usuarios/categorías/promociones y métricas con definiciones temporales; auditoría de acciones, permisos de cambio de estado y pruebas RLS por rol. No tomar cifras ficticias de las capturas como datos reales.
- [ ] **F14-BE-07 · Extras condicionales:** favoritos, notificaciones y promociones sólo tras decisión de alcance/operación; persistencia, disparadores, lectura/no lectura, vigencias y pruebas de autorización. Si se descartan, retirar controles y documentar el motivo.

## Lote F14-QA · Cierre y trazabilidad

- [ ] **F14-QA-01** Matriz `SRC/PDF página → captura → ruta → componente → contrato → RF/RN/DEC → prueba → evidencia` para los 54 recortes y pantallas PDF sin recorte; marcar diferencias aprobadas.
- [ ] **F14-QA-02** Regresión cliente/comercio/admin en dispositivo; estados de carga, vacío, error, offline y sesión vencida; texto al 200 %, TalkBack manual, cámara denegada, navegación Atrás y deep links.
- [ ] **F14-QA-03** Seguridad y concurrencia desde API/SQL: RLS de datos personales y globales, stock último ejemplar, QR/PIN de un uso, pago en efectivo antes de entrega, idempotencia y expiraciones por proceso del servidor.
- [ ] **F14-QA-04** Comparación visual por recorte y ruta, con captura real del mismo estado; registrar desvíos, causa y aceptación de Usuario. Cerrar cada tarea con `PASS/FAIL/NO_EJECUTADA` en [[05-Desarrollo/Testing]], [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

**Estado al redactar:** todos los ítems de F14 están `NO_EJECUTADA`; la evidencia de fases anteriores sirve como punto de partida de supervisión y no se reetiqueta automáticamente como cierre de F14.
