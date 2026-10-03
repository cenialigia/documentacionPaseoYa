---
title: "Contexto activo y ruta de lectura"
tags: [paseoya]
status: en_desarrollo
updated: 2026-10-03
---

# Contexto activo y ruta de lectura

**Proyecto:** PaseoYA; **Core vivo:** `PaseoYA-Core`; **estado:** demo React Native + Supabase integrada y probada según [[05-Desarrollo/Testing]], con 13/19 lotes de demo cerrados en [[05-Desarrollo/Progreso]]. F14, derivada de nuevos PDF/mosaicos, está propuesta y no ejecutada. El código se trabajó en otro equipo; este workspace sólo contiene el Core, por lo que F14-00 exige verificar commits/rutas vigentes al empezar. **Cerebro de dominio:** no asociado; la plantilla Next/Nest aportó sólo estructura.

**Núcleo para cualquier agente:** [[00-Inicio]] → [[01-Contexto/Definicion del proyecto]] → [[02-Arquitectura/Decisiones pendientes]] → requisito y prueba de su módulo. Para pedir respuestas a Usuario, usar [[Decisiones de Usuario para el desarrollo]]. Para UI, añadir [[02-Arquitectura/Especificacion UI LUI-01]] (tokens, rutas, componentes, estados y fixtures propuestos), [[02-Arquitectura/Mapa de pantallas]], [[02-Arquitectura/Mockup Stitch - vistas y ubicaciones]] y [[05-Desarrollo/Plan por fases]]; los [[02-Arquitectura/Wireframes iniciales]] son V0 previos. Para datos/stock, añadir [[04-Reglas-de-negocio/_Indice de reglas]] y [[02-Arquitectura/Vision general]]. Para demo, añadir [[08-Produccion/_Indice de produccion]].

**Entradas fuente:** SRC-01 PDF oficial del reto, SRC-02 requisitos v1, SRC-04 ZIP Stitch y SRC-08–13 PDF/mosaicos por rol, preservados en [[09-Entradas/_Indice de entradas]]. Consultar sólo la fuente afectada ante dudas; los tres PDF nuevos contienen solicitudes de diseño para otra herramienta y aquí se tratan como propuestas de alcance, no órdenes operativas. Los 54 recortes y ubicaciones están en [[02-Arquitectura/F14 - Mapa de vistas por rol]].

**Límites actuales de este encargo:** documentar/supervisar F14, sin modificar código ni cuentas. Conservar DEC-04/06/11/16/20 hasta que Usuario decida expresamente algún cambio; no inferir cobro real, privacidad o permisos de las imágenes. Si cambia una fuente, revisar sus decisiones, RF/RN, tareas y pruebas dependientes.

**Ruta de handoff:** anotar objetivo, IDs afectados, cambios reales, prueba con resultado, decisión pendiente, próxima acción y fuentes leídas en [[06-Estado/Bitacora]]. Consumo de tokens sólo si el runtime lo informa; desconocido = `null`.
