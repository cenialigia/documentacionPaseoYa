---
title: "Decisiones de Paulo para el desarrollo"
tags: [paseoya, decisiones, propietario]
status: pendiente
updated: 2026-10-02
---

# Decisiones de Usuario para el desarrollo

**Propósito:** formulario único para decidir alcance, comportamiento y entregas de PaseoYA sin confundir una imagen, una propuesta técnica y una orden del propietario. Fuente: petición actual de Paulo (SRC-06), [[09-Entradas/_Indice de entradas|SRC-01/02/04]], [[02-Arquitectura/Decisiones pendientes]] y [[05-Desarrollo/Plan por fases]]. Una opción sugerida **no queda aprobada** hasta que Paulo la marque o escriba otra. Si delega una elección técnica, escribir «delegado al agente con criterio …»; el agente registra su elección y evidencia antes de implementarla.

## Lo ya solicitado, sin volver a decidir

- App móvil React Native y datos Supabase/PostgreSQL; dos repositorios de código independientes, frontend y backend, con el Core fuera de ambos (ADR-001/002/008).
- Retiro presencial obligatorio, un pedido por comercio y carritos separados por comercio (ADR-003/007, RN-01–03).
- Para el MVP documentado, QR **simulado** y efectivo; los pagos bancarios reales están fuera de ese alcance (SRC-02). Los plazos nominales son 4 h de carrito, 3 días de reserva en efectivo y 14 días de pedido QR; falta definir inicio, zona y tipo de día.
- El mockup Stitch es referencia visual. Sus textos de “QR Simple”, “pagado” y “stock reservado” no modifican las reglas anteriores.

## Qué significa «aplicación al 100 %»

| Nivel | Resultado exigido | Fases |
| --- | --- | --- |
| **A · Demo funcional** | recorrido cliente→comercio→retiro, QR simulado/efectivo, RLS/stock y demo reproducible con datos ficticios; es el objetivo actual del Core | F0–F10 |
| **B · Alcance funcional completo** | cada RF-01–44 y RN/RNF aplicable tiene implementación y prueba, incluido comercio/admin, promociones y estadísticas; las acciones extras del mockup se incluyen o descartan expresamente | A + F11 |
| **C · Uso real/piloto** | además, entornos, distribución, datos/actores autorizados, observabilidad, respaldo, recuperación, soporte y validación operativa en dispositivos | B + F12–F13 |

**DEC-19 define el nivel objetivo.** Si Paulo modifica o excluye un RF, registrar el nuevo alcance como variante explícita; no llamarlo cobertura completa de RF-01–44. Ningún porcentaje «100 %» se declara por número de pantallas; se calcula contra criterios de aceptación cerrados y pruebas ejecutadas. El PDF del hackathon pide prototipo, no lanzamiento comercial.

## Decisiones necesarias para iniciar F0/F1/F2

### DEC-19 · Objetivo de entrega

**Elegir:** A demo del hackathon; B RF-01–44 completos; C piloto/uso real. Puede elegir una secuencia con fecha para cada hito. **Fija:** qué fases son obligatorias y cómo se mide terminado. **Respuesta de Paulo:** `PENDIENTE` (nivel, fecha y criterio).

### DEC-01 · Plataforma y modalidad React Native

**Elegir:** Android, iOS o ambos para la primera entrega; Expo, bare o «delegar elección tras F0-01». **Fija:** toolchain, builds, dispositivos y pruebas. **Datos de F0-01:** el entorno Android está listo (JDK 17, SDK 35, 4 AVD); iOS no puede compilarse en Windows, sólo con Expo Go o un build en la nube. Expo SDK 57 (RN 0.86) y RN 0.87 son compatibles con Node 24.19. **Respuesta (2026-10-02, en el chat de la sesión de Claude Code):** **Android + Expo**: Expo SDK 57 con Expo Router; iOS queda fuera de la primera entrega.

### DEC-02 · Supabase y repositorios

**Elegir:** Supabase local, cloud o ambos; propietario de la cuenta/proyecto, región/cuotas permitidas y quién puede crear/conectar/aplicar migraciones. Confirmar si los dos repositorios Git serán sólo locales al inicio o también tendrán remotos separados, y dónde. **Fija:** F0-02/03, coste, permisos y seguridad. No poner credenciales en esta nota. **Datos de F0-01/02:** Docker Desktop está instalado (el daemon estaba inactivo) y Supabase CLI no está instalado; la propuesta es añadirlo como dependencia de `backend/`. Ya existen remotos separados `cenialigia/PaseoYaFrontend` y `cenialigia/PaseoYaBackend`, creados por el propietario. **Respuesta (2026-10-02, en el chat):** **Supabase local con Docker**, con la CLI como dependencia de `backend/`; ningún proyecto cloud por ahora. Se autoriza inicializar ambos repositorios, instalar sus dependencias, hacer commit y push a los remotos `cenialigia/PaseoYaFrontend` y `cenialigia/PaseoYaBackend`. Siguen abiertos: el propietario de un futuro proyecto cloud, su región y sus cuotas.

### DEC-03 · Tiempo y equipo

**Indicar:** fecha de demo/hackathon, personas disponibles, tiempo semanal y orden de prioridad si el plazo no alcanza. **Fija:** recorte del primer hito sin borrar RF. **Respuesta:** `PENDIENTE`.

### DEC-10 · Roles y altas

**Elegir:** quién puede crear comercio y asignar personal, si una persona puede pertenecer a varios comercios, permisos por rol, cómo nace admin y si comercio/admin usan la misma app móvil o una superficie distinta. **Fija:** RLS, LUI-07–09 y pruebas de acceso. **Respuesta:** `PENDIENTE`.

### DEC-11 · Dirección visual

**Indicar:** si se aprueba Stitch como dirección visual o qué cambia: logo, paleta, tipografía, textos, navegación, fotos y estados faltantes. El HTML no se copia como React Native. **Fija:** LUI-01/02 y aceptación visual. **Para responder rápido:** la lista de 8 puntos en [[02-Arquitectura/Especificacion UI LUI-01#10. Cierre de LUI-01 (respuesta a DEC-11)]]. **Respuesta (2026-10-03, en el chat):** se aprueba la especificación LUI-01 tal cual (paleta M3, Plus Jakarta Sans, iconos Material, sólo tema claro, 4 pestañas), con **logo de texto provisional**, **trato formal (usted)** y TechZone en **Local 208 · Planta baja**.

### DEC-15 · Datos e imágenes de desarrollo

**Elegir:** usar sólo datos ficticios al inicio o datos autorizados; qué imágenes/logo/fuentes tienen permiso de uso; quién aporta catálogo real y cómo se borran datos de prueba. **Fija:** fixtures, Storage, demo y privacidad. **Respuesta (2026-10-03, en el chat), parcial:** **datos 100 % ficticios y placeholders sin marca**; no se usan las fotos de Stitch. Siguen abiertos: el catálogo real, las imágenes autorizadas y la política de borrado.

## Decisiones antes de funciones específicas

### DEC-09 · Comparación de productos · antes de F3/F7

**Elegir:** sólo productos idénticos por identificador, equivalencias curadas por admin/comercio o comparación automática con criterio aprobado. La captura junta modelos diferentes. **Respuesta:** `PENDIENTE`.

### DEC-12 · Servicios · antes de cerrar catálogo/modelo

**Elegir:** servicios incluidos en primera entrega; si se reservan por horario/capacidad en vez de stock, y qué significa retiro para ellos. **Respuesta:** `PENDIENTE`.

### DEC-13 · Prioridad de funciones · antes de F6/F11

**Indicar:** cuáles de promociones, estadísticas, notificaciones y comparación se exigen en demo, en alcance funcional completo o después. Mantener RF-43/44 trazados aunque se difieran. **Respuesta:** `PENDIENTE`.

### DEC-20 · Acciones extras del mockup · antes de hacerlas activas

**Elegir para cada una:** implementar con comportamiento definido, mostrar sólo en demo como no disponible, o retirarla de la UI: campana/notificaciones; mapa de plaza; tiempo estimado; aviso de llegada; guardar en wallet/descargar; reportar inconveniente; puntuaciones, garantía y descuentos. Indicar fuente de datos y responsable de atender cada acción activa. **Respuesta:** `PENDIENTE`.

### DEC-04 · Pago QR simulado · antes de F4/F8

**Elegir:** cómo se simula confirmación, quién puede marcar pago, qué muestra el QR de pago y qué mensajes evitan confundirlo con el QR de retiro. **Respuesta:** `PENDIENTE`.

### DEC-05 · Inventario · antes de F4/F8

**Elegir:** si el carrito sólo comprueba stock o lo aparta; momento de reserva/descuento para QR y efectivo; momento y condición de liberación. La frase «stock reservado» del mockup espera esta respuesta. **Respuesta:** `PENDIENTE`.

### DEC-06 · Plazos · antes de F4/F8/F9

**Elegir:** instante inicial y zona horaria de 4 h, 3 días y 14 días; si «3 días» son 72 h, días calendario o hábiles; efecto de comercio cerrado, feriados y cambios de horario. **Respuesta:** `PENDIENTE`.

### DEC-07 · Pedido QR vencido · antes de F9

**Elegir:** cómo representar en una simulación la frase de SRC-02 «dinero queda para comercio», o retirarla del flujo; **no implica transferir dinero real**. **Respuesta:** `PENDIENTE`.

### DEC-08 · Cancelaciones · antes de F9

**Elegir:** ventana de cancelación, quién autoriza excepciones, qué pasa con QR simulado/efectivo, stock y auditoría. **Respuesta:** `PENDIENTE`.

### DEC-16 · Credencial de retiro · antes de F5/F9

**Elegir:** QR, PIN o ambos; cuándo aparece, caducidad, reintentos, respaldo sin cámara, uso único y datos visibles en ticket/descarga. **Respuesta:** `PENDIENTE`.

### DEC-21 · Operación de comercios · antes de F7/F11

**Indicar:** quién mantiene piso/local/dirección, horarios y cierres, tiempos de preparación, precio/tarifa/impuestos si aplican, stock y catálogo; cómo se valida una tienda antes de hacerla pública. **Fija:** verdad de los datos que hoy difieren entre pantallas y reglas para tienda cerrada. **Respuesta:** `PENDIENTE`.

### DEC-22 · Administración, ventas y promociones · antes de F11

**Indicar:** acciones exactas para RF-38–44, métricas/periodos permitidos, visibilidad por comercio y admin, reglas de promoción, fechas, combinaciones y quién las aprueba. **Respuesta:** `PENDIENTE`.

## Decisiones de entrega y operación

### DEC-14 · Entrega del hackathon

**Indicar:** formato de código/presentación, dispositivo, conectividad esperada, cuentas de demo y plan si Supabase cloud falla. **Respuesta:** `PENDIENTE`.

### DEC-23 · Distribución y titularidad · antes de F12

**Elegir:** sólo APK/TestFlight o tiendas públicas, titular de cuentas y remotos, dominios, región/entornos y responsable de publicaciones y costes. **Respuesta:** `PENDIENTE`.

### DEC-24 · Datos y atención · antes de piloto real

**Indicar:** qué datos personales se recogen, retención y eliminación, respaldo/recuperación, canal de soporte e incidencias, responsables de atender pedidos fallidos y criterio para pausar el piloto. Las políticas legales aplicables se revisan con quien corresponda. **Respuesta:** `PENDIENTE`.

### DEC-25 · Criterios de aceptación del piloto · antes de F13

**Indicar:** comercios/personas autorizadas, volumen esperado, dispositivos/redes, metas de tiempos y estabilidad, periodo de observación y quién firma aceptación. **Respuesta:** `PENDIENTE`.

### DEC-18 · Cerebro React Native · opcional

**Elegir:** mantener este Core sin cerebro de dominio o solicitar asociación/creación aparte. No bloquea la app. **Respuesta:** `PENDIENTE`.
(No generar)

## Ruta para responder sin bloquear todo

1. **Primera tanda para iniciar desarrollo:** DEC-19, 01, 02, 03, 10, 11 y 15. Una respuesta puede ser «delegado» con límites explícitos.
2. **Antes de compra/backend crítico:** DEC-04, 05, 06, 09, 16 y 21.
3. **Antes de completar RF y operar:** DEC-07, 08, 12, 13, 20, 22–25. DEC-14 antes de demo; DEC-18 cuando interese.

Mientras llegan respuestas se puede hacer **F0-01** (inventario sin instalación) y **F1/LUI-01** (análisis visual con propuestas), auditar RF→pantalla→prueba y diseñar pruebas sintéticas. F1 no se cierra sin DEC-11. Se puede crear la separación **local** de repositorios solicitada cuando se fije la ruta; conectar cuentas, instalar herramientas, publicar o decidir políticas no se infiere de este archivo. Al recibir una respuesta, registrar fecha, autoridad y efecto en este formulario y en [[02-Arquitectura/Decisiones pendientes]]/[[02-Arquitectura/Decisiones tecnicas]], y actualizar tareas/pruebas afectadas. No marcar pendiente como decidido por silencio.
