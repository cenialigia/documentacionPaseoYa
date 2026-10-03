---
title: "Procedencia de la semilla y mapa de superficies"
tags: [paseoya, metodologia, procedencia]
status: vigente-documental
updated: 2026-10-02
---

# Procedencia de la semilla y mapa de superficies

**Raíz objetivo autorizada:** `E:/Repositorios/Hackathon/PaseoYA`. **Core vivo:** `PaseoYA-Core`. **Propietario/integrador inicial:** Usuario. **Identidad provisional:** `LIVE_CORE:paseoya`; no consta todavía en el catálogo del Manager. **Cerebro de dominio:** `unknown`. Manager y plantilla Next/Nest ofrecen método y organización, no reglas técnicas de React Native.

**Fuente estructural exclusiva:** `E:/Repositorios/CORES/nextjs+nestjs/Plantilla-Core-Proyecto`, revisión Git consultada `0f45b9267090e121840686802d5ffe91ad4a23e9` (24 archivos). Se replicaron los nombres y superficies de la semilla aplicables al Core; se reescribió el contenido de producto para este reto. No se copió el cerebro completo. Los tres archivos `_Plantilla` permanecen como ejemplos editables, con marcadores legítimos de plantilla. Se añadieron notas expresamente necesarias para decisiones, contexto, plan y diseño visual por la petición actual.

## Mapeo del inventario original

| Origen en Plantilla-Core-Proyecto | Destino / tratamiento |
| --- | --- |
| `00-Inicio.md` | `PaseoYA-Core/00-Inicio.md` |
| `COPIAR-ESTA-CARPETA.md` | no copiado: instrucción de generación, sin utilidad dentro del Core vivo |
| `01-Contexto/Definicion del proyecto.md` | mismo relativo en Core |
| `01-Contexto/Glosario.md` | mismo relativo en Core |
| `02-Arquitectura/Decisiones tecnicas.md` | mismo relativo en Core |
| `02-Arquitectura/Vision general.md` | mismo relativo en Core |
| `03-Modulos/_Indice de modulos.md` | mismo relativo en Core |
| `03-Modulos/_Plantilla de modulo.md` | mismo relativo en Core, plantilla genérica |
| `04-Reglas-de-negocio/_Indice de reglas.md` | mismo relativo en Core |
| `04-Reglas-de-negocio/_Plantilla de regla.md` | mismo relativo en Core, plantilla genérica |
| `05-Desarrollo/Criterio de terminado.md` | mismo relativo en Core |
| `05-Desarrollo/Entorno local.md` | mismo relativo en Core |
| `05-Desarrollo/Ramas y entregas.md` | mismo relativo en Core |
| `05-Desarrollo/Testing.md` | mismo relativo en Core |
| `06-Estado/Bitacora.md` | mismo relativo en Core |
| `06-Estado/Tareas pendientes.md` | mismo relativo en Core |
| `07-Manuales/Manual de usuario.md` | mismo relativo en Core |
| `07-Manuales/Mantenimiento del manual.md` | mismo relativo en Core |
| `08-Produccion/_Indice de produccion.md` | mismo relativo en Core |
| `09-Entradas/_Indice de entradas.md` | mismo relativo en Core |
| `09-Entradas/_Plantilla de entrada.md` | mismo relativo en Core, plantilla genérica |
| `10-Metodologia/Metodo del proyecto.md` | mismo relativo en Core |
| `_Raiz-del-proyecto/AGENTS.template.md` | `PaseoYA/AGENTS.md` |
| `_Raiz-del-proyecto/CLAUDE.template.md` | `PaseoYA/CLAUDE.md` |

**Altas autorizadas por esta solicitud:** `01-Contexto/Contexto activo.md`, `02-Arquitectura/Decisiones pendientes.md`, `02-Arquitectura/Mapa de pantallas.md`, `02-Arquitectura/Wireframes iniciales.md`, `05-Desarrollo/Plan por fases.md`, `05-Desarrollo/Progreso.md`, esta nota y las dos fuentes originales preservadas en `09-Entradas`. Ninguna alta cambia la plantilla del cerebro.

## Perfil de las diez superficies

| Superficie | Ruta principal | Estado documental | Criterio actual |
| --- | --- | --- | --- |
| Identidad y visión | [[01-Contexto/Definicion del proyecto]] | vigente | objetivo, usuarios, problema y demo trazados |
| Alcance | [[01-Contexto/Definicion del proyecto]] | vigente | incluido, diferido, restricciones y dudas |
| Requisitos y decisiones | [[03-Modulos/_Indice de modulos]] · [[02-Arquitectura/Decisiones pendientes]] | vigente | RF/RN enlazados y pendientes identificados |
| Sistema y diagramas | [[02-Arquitectura/Vision general]] | borrador | componentes e invariantes propuestos; ERD falta para F7 |
| Desarrollo | [[05-Desarrollo/Plan por fases]] · [[05-Desarrollo/Progreso]] | vigente | tareas, dependencias y próxima fase |
| Calidad | [[05-Desarrollo/Testing]] | vigente | casos definidos; resultados NO_EJECUTADOS |
| Contexto | [[01-Contexto/Contexto activo]] · [[09-Entradas/_Indice de entradas]] | vigente | ruta mínima y originales recuperables |
| Operación y documentación | [[08-Produccion/_Indice de produccion]] · [[07-Manuales/Manual de usuario]] | borrador | demo y manual planeados; producto inexistente |
| Sesiones y orquestación | [[05-Desarrollo/Plan por fases]] · [[06-Estado/Bitacora]] | vigente | integrador, puertas y handoff documentados |
| Evolución | [[06-Estado/Bitacora]] | borrador | procedencia inicial; aprendizaje de ejecución aún ninguno |

`vigente` califica una **nota documental personalizada**, no una capacidad de la aplicación. Para formalizar un `ProjectManifest/v1` con `brain_ref` de dominio no inventado, resolver DEC-18. Hasta entonces esta nota es el manifiesto legible y declara el hueco.
