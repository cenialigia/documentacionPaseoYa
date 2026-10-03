---
title: "Plan por fases y lotes UI/backend"
tags: [paseoya, plan]
status: planificado
updated: 2026-10-03
---

# Plan por fases y lotes UI/backend

**IDs:** `UI-01`–`UI-10` nombran pantallas del [[02-Arquitectura/Mapa de pantallas]]; `LUI-01`–`LUI-10` nombran **lotes de trabajo**. `BE`, `COMP`, `OPS` y `PIL` nombran otros lotes. Así una captura no se confunde con una tarea cerrada.

**Plan original:** Paulo pidió interfaz desde [[02-Arquitectura/Mockup Stitch - vistas y ubicaciones|SRC-04]], backend y F0 con repositorios separados. P-00 fue la semilla documental previa. F0–F10 conducen a demo MVP; F11–F13 amplían cobertura y piloto. **Estado real posterior:** F0 cerrada y demo integrada parcialmente cerrada según [[05-Desarrollo/Progreso]]/[[05-Desarrollo/Testing]]. Las tablas de esta nota conservan el plan inicial; para los PDF y 54 vistas nuevos usar [[05-Desarrollo/F14 - Revision y ampliacion por roles]].

## Destino de artefactos al ejecutar

| Superficie | Ubicación lógica propuesta | Contenido | Estado |
| --- | --- | --- | --- |
| Documentación | `PaseoYA-Core/` bajo esta raíz | requisitos, decisiones, mockups, evidencia, handoff | existente |
| Cliente | `PaseoYA-frontend/` como **repositorio Git independiente** | React Native, navegación, componentes, assets, pruebas de UI | pendiente F0 |
| Backend | `PaseoYA-backend/` como **repositorio Git independiente** | configuración Supabase local, migraciones SQL, RLS, funciones/operaciones confiables y pruebas | pendiente F0 |

Los dos repositorios de código tendrán historias y remotos propios si Paulo autoriza remotos. El Core queda fuera de ambos. **Supabase es servicio/plataforma, no un repositorio Git remoto por sí mismo**; su definición reproducible vive en `PaseoYA-backend/`. Node.js se verifica como herramienta para React Native y tooling/backend; un servidor Node adicional no se presupone. F0 documenta versiones compatibles y decide Expo/bare, Supabase local/cloud y propietario de los recursos con DEC-01/02 antes de inicializar o conectar. Las rutas exactas y remotos se registrarán al crearlos.

## Secuencia y puertas

| Fase | Lotes y resultado aceptable | Depende de | Puerta / prueba planeada |
| --- | --- | --- | --- |
| **F0 · Preparación técnica** | F0-01 inventario Node.js, gestor, React Native/Android-iOS, Supabase CLI y dispositivo; F0-02 dos repositorios independientes; F0-03 bootstrap reproducible y variables de ejemplo sin secretos | P-00, DEC-01/02 para elecciones con efecto | evidenciar comandos/versiones, arranque mínimo en dispositivo y migración local si se autoriza; `NO_EJECUTADA` mientras no se haga |
| **F1 · Especificación UI** | LUI-01 inventario de 6 capturas + shell, rutas, tokens, componentes, assets/licencias, datos ficticios coherentes y estados faltantes | SRC-04, RF/RN/DEC; aprobación DEC-11 para cerrar | Paulo valida dirección visual y puntos MK-01–08; comparación con mockup y T-UI documental |
| **F2 · Base de interfaz** | LUI-02 shell cliente, navegación de 4 pestañas, stacks, tema, componentes, datos fixture y accesibilidad básica | F0, LUI-01/DEC-11 | build móvil y navegación con lector de pantalla/tamaños táctiles |
| **F3 · Descubrimiento** | LUI-03 Explorar, tienda, detalle de producto faltante, búsqueda/comparación y filtros | LUI-02, DEC-09 para equivalencias | T-UI/T-CAT con fixtures: rutas, vacíos, agotado, sin red |
| **F4 · Compra visual** | LUI-04 carritos por tienda y temporizadores; LUI-05 checkout, selector QR simulado/efectivo y estados de confirmación | LUI-02/03, DEC-04–06 | T-UI/T-CART/T-CHECKOUT con fixtures; sin declarar stock real |
| **F5 · Seguimiento y retiro visual** | LUI-06 Mis pedidos, historial, ticket QR/PIN ilustrativo, ubicación e incidencias | LUI-02/05, DEC-16 | T-UI; credencial de fixture inequívocamente no válida |
| **F6 · Cobertura UI restante** | LUI-07 acceso/cuenta, LUI-08 comercio catálogo/cola/retiro, LUI-09 admin según alcance, LUI-10 revisión responsive/accesibilidad y capturas | LUI-02, RF-01–04/27–44, DEC-10/13 | T-UI; Paulo acepta superficies no representadas en Stitch |
| **F7 · Base backend** | BE-01 esquema/migraciones/Auth/RLS; BE-02 comercios, productos, búsqueda/comparación y datos ficticios | F0 + F1 aceptada, decisiones de datos/roles | T-RLS con llamadas directas y T-CAT; ningún secreto en Core |
| **F8 · Transacciones backend** | BE-03 carritos, checkout por comercio, pedido/pago separado, stock atómico e idempotencia | BE-01/02, DEC-04–06/09 | T-CART/T-ORD/T-CHECKOUT/T-STOCK con acceso y concurrencia |
| **F9 · Operación backend** | BE-04 cola de comercio, transición, credencial de retiro de un uso, cancelación y expiraciones programadas | BE-03, DEC-06–08/16 | T-RET/T-CAN/T-EXP sin depender de app abierta |
| **F10 · Integración y demo** | INT-01 sustituir fixtures por contratos de backend; INT-02 pruebas por rol/dispositivo, correcciones, manual, entrega y demo | LUI-03–10 + BE-01–04 | T-UI/T-RLS/T-STOCK/T-DEMO y evidencia de build/flujo real |
| **F11 · Cobertura funcional completa** | COMP-01 gestión comercial/ventas; COMP-02 operaciones admin/estadísticas/promociones; COMP-03 extras y servicios aprobados; COMP-04 matriz RF/RN/RNF y regresión | F10 + DEC-12/13/20/21/22 | T-FULL; cada RF-01–44 implementado y probado; extras según decisión |
| **F12 · Preparación para uso real** | OPS-01 ambientes, distribución y reversa; OPS-02 seguridad, rendimiento, accesibilidad, respaldo, privacidad, soporte y observabilidad | F11 + DEC-23/24 | T-OPS; restauración y respuesta a fallos ensayadas, builds firmadas según destino |
| **F13 · Piloto y aceptación** | PIL-01 datos/comercios autorizados, capacitación y UAT; PIL-02 salida controlada, seguimiento, correcciones y aceptación | F12 + DEC-25 | T-PIL; evidencia de flujo real y firma del responsable |
| **F14 · Revisión y ampliación por roles** | F14-00 decisiones/inventario; UI Cliente 26, Comercio 14, Admin 14 tareas por captura + X-01–06 sin captura; BE-01–07 y QA-01–04 | demo integrada existente como base de supervisión; decisiones DEC-F14 por lote | evidencia por ruta/estado, RLS/concurrencia y comparación visual; íntegra en [[05-Desarrollo/F14 - Revision y ampliacion por roles]] |

**Grafo original:** F0 y F1 pueden avanzar en paralelo; F0 + F1 → F2 → F3 → F4 → F5; F2 → F6; F0 + F1 → F7 → F8 → F9; LUI-03–10 + BE-01–04 → F10 → F11 → F12 → F13. **F14 se abre como línea de ampliación desde el estado integrado actual, tras su propia puerta de decisiones e inventario; no depende de cerrar F11–13.**

## Lotes de UI: entregables concretos

| Lote | Tareas a realizar | RF/RN/DEC | Criterio de aceptación |
| --- | --- | --- | --- |
| LUI-01 | Auditar cada elemento de SRC-04; resolver MK-01–08; definir tokens con contraste, tamaños, copy, mapa de navegación, estados y fixtures por comercio/pedido; aprobar assets/licencias. | RF-01–44 según vista; DEC-09/11/15 | especificación y matriz vista→componente→estado→acción; Paulo registra decisiones pendientes |
| LUI-02 | Crear shell cliente, header, campana/cuenta como rutas explícitas, pestañas Explorar/Comparar/Carritos/Pedidos, contadores y stacks; componentes Card/Chip/Button/Price/Status/Loading/Error. | RNF-07/09, DEC-01/10/11 | volver atrás conserva estado, no duplica checkout; controles táctiles/lector de pantalla |
| LUI-03 | Explorar: hero/categorías/tiendas/ofertas; Comparar: búsqueda/filtros/resumen/tarjetas por comercio; crear detalle y tienda faltantes; manejar datos vacíos y stock. | RF-05–13, DEC-09 | acción de cada tarjeta lleva al comercio y carrito correctos; comparación no mezcla variantes no homologadas |
| LUI-04 | Dos o más carritos simultáneos, subtotal por tienda, cantidad/eliminar, reloj de expiración, ubicación y CTA de checkout por carrito; no afirmar reserva de stock antes de DEC-05. | RF-13–17, RN-02–05 | editar uno no modifica otro; caducidad/stock cambiante visible y recuperable |
| LUI-05 | Resumen de un comercio, punto de entrega, selector QR simulado/efectivo, plazos/copy según DEC-04–06, estados procesando/error/reintento y confirmación. | RF-18–22, RN-02/06/07 | total y local únicos; doble toque no dispara dos pedidos; pago y retiro se distinguen visualmente |
| LUI-06 | En curso/historial, tarjeta por pedido/estado, ticket con QR/PIN ilustrativo, ubicación, límite y acciones priorizadas; sin exponer credencial en fixtures productivos. | RF-23–26, RN-01, DEC-16 | navegación pedido→ticket consistente; cancelado/expirado/entregado no ofrece código válido |
| LUI-07 | Registro, login, perfil, sesión vencida y recuperación; permisos reflejados en navegación sin sustituir RLS. | RF-01–04, DEC-10 | cada rol ve entradas correctas; mensajes de error y accesibilidad |
| LUI-08 | Comercio: catálogo, precio/stock, pedidos nuevos/preparando/listos, validación presencial QR/PIN y errores. | RF-27–38, RN-01/09 | prototipo cubre entrega una vez y rechazo de código ajeno/expirado |
| LUI-09 | Admin: usuarios, comercios, categorías, pedidos y métricas según priorización acordada. | RF-39–44, DEC-10/13 | alcance y acceso aprobados; no extrapolar la barra cliente a admin |
| LUI-10 | Revisar escala móvil/tablet acordada, contraste, textos truncados, tamaños táctiles, lector, offline, capturas y comparación con SRC-04. | RNF-07/09, DEC-11/15 | T-UI ejecutada y diferencias aprobadas o registradas |

## Lotes backend: contratos y pruebas

| Lote | Tareas a realizar | Criterio de aceptación |
| --- | --- | --- |
| BE-01 | Migraciones versionadas para identidad, comercios, membresías, catálogo, carritos, órdenes, pagos y credenciales; Auth y RLS por cliente/comercio/admin; política Storage si se usa. | migración reproducible; T-RLS rechaza lecturas/escrituras cruzadas por API directa |
| BE-02 | Lectura de catálogo, categorías, disponibilidad y búsqueda; contrato de equivalencia DEC-09, imágenes autorizadas, seed sintético consistente. | T-CAT; precios/locales/stock coherentes en todas las vistas |
| BE-03 | Mutaciones de carrito; checkout atómico de **un comercio** con snapshot de precio, pago QR simulado o efectivo, reserva/descuento según DEC-05, clave idempotente y auditoría. | T-CART/T-ORD/T-CHECKOUT/T-STOCK; dos compras concurrentes de la última unidad no sobrevenden |
| BE-04 | Transiciones de preparación, validación QR/PIN de un uso por comercio dueño, cancelación, liberación de stock y expiraciones 4 h/3 d/14 d según DEC-06–08. | T-RET/T-CAN/T-EXP; reejecución no duplica efectos y no depende del móvil abierto |

Antes de programar operaciones críticas, elegir y registrar si se implementan como función SQL, Edge Function o API confiable. Ninguna escritura de stock o cambio de rol depende sólo del cliente móvil.

## Lotes adicionales para alcance B/C

| Lote | Trabajo que falta hacer explícito | Aceptación |
| --- | --- | --- |
| COMP-01 | Backend y UI de alta/edición/precio/stock/activación de productos por comercio (RF-27–31), datos de tienda/horarios y consulta de ventas (RF-38). | permisos por comercio, cambios auditados, stock consistente y T-FULL |
| COMP-02 | Backend y UI de gestión de usuarios/comercios/categorías/pedidos, estadísticas y promociones (RF-39–44); reglas y métricas según DEC-22. | T-RLS y T-FULL con roles; estadísticas coherentes y promociones con vigencia verificable |
| COMP-03 | Resolver y, si se aprueban, implementar servicios y acciones Stitch: notificaciones, mapa, ETA, aviso de llegada, wallet/descarga, incidencias, puntuación, garantías y descuentos. | cada control visible tiene destino real o queda retirado; prueba y fuente de datos por función |
| COMP-04 | Matriz RF-01–44/RN/RNF → UI/API/migración → prueba → evidencia; cerrar huecos y regresión de extremos por rol y dispositivo. | ningún RF-01–44 queda sin evidencia PASS; toda excepción cambia explícitamente el alcance B |
| OPS-01 | Entornos dev/staging/producción, build firmado, publicación/distribución, CI, configuración, migraciones reversibles y rollback. | despliegue y reversa ensayados sin datos reales no autorizados |
| OPS-02 | Revisión de seguridad y privacidad, rendimiento/carga, accesibilidad, monitoreo/alertas, respaldo/restauración, soporte e incidentes. | T-OPS en entorno elegido; responsables y límites documentados |
| PIL-01 | Incorporación autorizada de comercios, catálogo y usuarios reales; capacitación y aceptación de recorridos. | UAT por cliente/comercio/admin con datos autorizados |
| PIL-02 | Salida controlada, observación de errores, correcciones y aceptación del propietario. | T-PIL y decisión de continuar, ajustar o detener |

## Qué puede arrancar ahora

- **Sin decisiones adicionales:** F0-01 inventario de herramientas **sin instalar** y F1/LUI-01 análisis de tokens/estados y comparación detallada con Stitch; matriz RF→pantalla→prueba y especificación de pruebas sintéticas. F1 sólo se cierra después de DEC-11. Ninguna de estas tareas afirma producto implementado.
- **Con decisión breve de plataforma/ruta (DEC-01/02):** F0-02/03, dos repositorios locales e inicio reproducible. Con DEC-11 puede arrancar F2 y la UI de Explorar usando fixtures.
- **Al cerrar reglas concretas:** F3 comparación tras DEC-09; F4/F8 tras DEC-04–06; F5/F9 tras DEC-16; comercio/admin tras DEC-10/13/21/22. F11–F13 requieren primero elegir alcance en DEC-19.

## Ejecución y estado

- Cada lote tiene **un responsable escritor** y un integrador del Core; asignación concreta al iniciar. Dependencias aceptadas y archivos permitidos se fijan en el paquete de trabajo; no hay dos agentes mutando la misma migración.
- Puertas humanas: DEC-01/02 para F0; DEC-04–06/09/11/15 para UI y datos; DEC-10/13/16 para roles y retiro. Una puerta detiene sólo los lotes afectados.
- **Orquestación, reevaluación 2026-10-02:** siguen presentes dependencias, varias sesiones previstas, decisiones humanas y efectos futuros. Se mantiene coordinación explícita **por archivos del Core** (este grafo, bitácora y pruebas), sin runtime instalado. Persistencia: notas del Core; alternativa ante falta de herramienta auxiliar: trabajo secuencial por archivos. Si se automatizan tareas con efectos o varios agentes escriben concurrentemente, se decide entonces mecanismo de exclusión/reintento con versión y aprobación.
- Cierre de cada fase: salida real, `PASS/FAIL/NO_EJECUTADA` y límite de prueba en [[05-Desarrollo/Testing]], estado de casillas en [[06-Estado/Tareas pendientes]], [[05-Desarrollo/Progreso]] y [[06-Estado/Bitacora]].

## Registro histórico de recorte por plazo (DEC-03: entrega en menos de 1 día, 2 personas) · 2026-10-03

Aprobado entonces en el chat: **app simulada completa + backend Supabase aparte**. Esta tabla refleja aquel recorte; posteriormente INT-01 sí se implementó y se probó, según [[05-Desarrollo/Testing]].

| Orden | Lote | Contenido mínimo para la demo | Estado |
| --- | --- | --- | --- |
| D1 | Ajustes por decisiones | pestaña «Buscar» en lugar de Comparar (DEC-09); quitar Avisos (DEC-20); perfil con «Reportar problema»; detalle con «Simular pago» (DEC-04) y cancelación en Confirmado (DEC-08); ticket con QR + PIN (DEC-16) y «Guardar ticket» | hecho · frontend `c0040b1` |
| D2 | Acceso por rol (LUI-07 mínimo) | login con cuentas de demostración CLIENTE / COMERCIO (TechZone) / ADMIN, registro de cliente y redirección por rol (DEC-10) | hecho |
| D3 | Panel de comercio (LUI-08 mínimo) | cola de pedidos de su comercio: iniciar preparación → marcar listo → validar PIN → entregado; confirmar efectivo | hecho · EVID-DEMO-a |
| D4 | Admin mínimo (LUI-09) | listado de comercios y supervisión de pedidos (sólo lectura) | hecho |
| B1 | Backend (BE-01/03/04 mínimo) | migración con perfiles/roles, comercios, productos, pedidos y credenciales; RLS por rol y `comercio_id`; funciones `confirmar_pedido` (stock atómico e idempotente), `simular_pago`, transiciones, `validar_retiro`, `cancelar_pedido`; seed ficticio; pruebas SQL de RLS y concurrencia | hecho · backend `2475598`, EVID-BE-a/b/c |

Fuera del plazo: integración real (INT-01), expiraciones programadas, estadísticas, promociones y la pasada manual con TalkBack.
