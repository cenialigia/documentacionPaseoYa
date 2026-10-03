---
title: "Decisiones pendientes del propietario"
tags: [paseoya]
status: planificado
updated: 2026-10-02
---

# Decisiones pendientes del propietario

No bloquear trabajo documental ni pruebas sintéticas por preguntas abiertas. **Antes de implementar lo que dependa de una decisión, pedirla a Paulo con opciones y efecto.** IDs estables para no repetir el cuestionario. Formulario completo, opciones y orden de respuesta: [[Decisiones de Usuario para el desarrollo]].

| ID | Pregunta concreta | Impacto / propuesta para revisar |
| --- | --- | --- |
| DEC-01 | **Resuelta 2026-10-02:** Android + Expo (ver formulario). | F0 debe registrar compatibilidad/versiones Node.js y toolchain; build, pruebas en dispositivo y estructura inicial. Expo es candidato, no aprobado. |
| DEC-02 | **Resuelta en parte 2026-10-02:** Supabase local con Docker; remotos Git autorizados. Queda abierto el proyecto cloud: propietario, región, cuotas y protección de claves. | F0 inicializa repositorio backend **separado** según autorización; proyecto cloud, remotos, coste, permisos, migraciones, funciones de checkout y expiraciones se deciden explícitamente. Supabase no exige por sí solo servidor Node. |
| DEC-03 | ¿Cuándo es el hackathon, tamaño del equipo y tiempo real disponible? | Priorizar RF-01–44 sin presentar todo como imprescindible para la primera demo. |
| DEC-04 | ¿Cómo se confirma el pago QR simulado y quién puede cambiarlo? ¿Qué representa exactamente el QR de pago? | Evita confundir pago con código de retiro. |
| DEC-05 | ¿Cuándo se reserva stock para QR y efectivo, y cuándo se descuenta? | SRC-04 muestra “stock reservado” ya en carrito; es sólo copy del mockup hasta resolver modelo y transacción atómica, sobreventa y doble liberación. |
| DEC-06 | ¿Desde qué instante y zona horaria corren 4 h de carrito, 3 d efectivo y 14 d QR? ¿Qué pasa si el comercio está cerrado? | SRC-04 alterna “3 días”, “72 horas” y “3 días hábiles”; resolver antes de copy final, cálculo y prueba de vencimiento. |
| DEC-07 | ¿Es política aprobada que un QR simulado vencido “quede para el comercio”? ¿Cómo se representa sin dinero real? | Afirmación sólo del MD §8; requiere decisión comercial antes de modelarla. |
| DEC-08 | ¿Qué cancelaciones excepcionales/reembolsos simulados y quién las autoriza? | Transiciones, auditoría y stock. |
| DEC-09 | ¿Cómo se emparejan productos equivalentes de distintos comercios? ¿Comparación manual o automática? | SRC-04 compara modelos diferentes de audífonos; no declarar equivalencia por simple categoría o texto. Buscador global y RF-10. |
| DEC-10 | ¿Qué comercio/persona accede a cada dato y cómo se da de alta? ¿Administrador móvil o superficie separada? | Roles, RLS, pantallas y pruebas. |
| DEC-11 | ¿Qué elementos de SRC-04 se aprueban: logo, paleta, tipografía, fotos, tono, navegación y textos? | [[02-Arquitectura/Mockup Stitch - vistas y ubicaciones]] y [[02-Arquitectura/Wireframes iniciales]] son referencias; `DESIGN.md` y HTML difieren en tokens. |
| DEC-12 | ¿Pedidos de servicios tienen stock, horario y retiro igual que productos? | El PDF incluye servicios; el MD modela unidades físicas. |
| DEC-13 | ¿Promociones, estadísticas, notificaciones y comparación entran en demo o versión posterior? | Equilibrio entre reto oficial y tiempo disponible. |
| DEC-14 | ¿Cómo se entregan presentación, repositorio y demo? ¿Habrá conectividad y dispositivos durante la defensa? | Plan de contingencia y evidencia. |
| DEC-15 | ¿Qué datos ficticios, imágenes/licencias y políticas de retención se permiten? | Seed de demo y privacidad. |
| DEC-16 | ¿QR de retiro, PIN o ambos? ¿Caducidad, reintentos y método de respaldo? | Riesgo de entrega indebida. |
| DEC-18 | ¿Crear/asociar un cerebro React Native o mantener este Core sin cerebro de dominio por ahora? | El catálogo marca Android como reservado/vacío; la plantilla Next/Nest aquí sólo aportó estructura. El Manager podrá registrar asociación cuando Paulo la elija. |
| DEC-19 | ¿La meta es demo A, cobertura funcional B o piloto real C? ¿Con qué fecha y aceptación? | Activa F11–F13 y define el denominador de «100 %». |
| DEC-20 | ¿Cuáles acciones extras de Stitch funcionan, se difieren o se quitan? | Notificaciones, mapa, ETA, llegada, wallet/descarga, incidencias, puntuación/garantía/descuentos. |
| DEC-21 | ¿Quién mantiene horarios, locales, precios, stock y catálogo, y cómo se publica un comercio? | Fuente de verdad y operación comercial; F7/F11. |
| DEC-22 | ¿Qué operaciones, métricas y promociones exactas tendrá administración y consulta de ventas? | RF-38–44; F11. |
| DEC-23 | ¿Cómo se distribuye la app y quién es titular de cuentas, remotos y costes? | F12, publicación y entornos. |
| DEC-24 | ¿Cómo se tratan datos personales, retención, respaldo, soporte e incidencias? | F12/F13; política operativa. |
| DEC-25 | ¿Con qué comercios, dispositivos, volumen y metas se acepta el piloto? | F13, UAT y firma de cierre. |

DEC-17 queda **resuelta por SRC-02**: varios carritos y un pedido por comercio son requisitos expresos RN-02/03; se conserva el ID histórico sin volver a preguntarlo. El PDF oficial manda en condiciones del reto; el MD contiene requisitos de Paulo. Ninguno concede permiso de conectar servicios, hacer pagos reales o publicar.
