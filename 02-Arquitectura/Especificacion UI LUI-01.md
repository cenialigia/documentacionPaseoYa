---
title: "Especificación UI · LUI-01"
tags: [paseoya, ui, especificacion]
status: aprobado
updated: 2026-10-03
---

# Especificación UI · LUI-01

**Estado:** **aprobada por Usuario el 2026-10-03** (DEC-11 y DEC-15, en el chat de la sesión), con dos cambios: trato **formal (usted)** y TechZone en **Local 208 · Planta baja**. El logo es texto provisional y las imágenes son placeholders sin marca. Construida a partir de [[02-Arquitectura/Mockup Stitch - vistas y ubicaciones|SRC-04]], [[02-Arquitectura/Mapa de pantallas]] y los RF/RN de SRC-02. LUI-01 queda cerrada; esta nota es la referencia de LUI-02 y siguientes. Las decisiones de negocio pendientes (DEC-04/05/06/09/16) aparecen como marcadores, nunca como reglas.

## 1. Tokens de diseño propuestos

**Fuente canónica:** la paleta Material 3 que comparten los seis HTML y el front matter de `DESIGN.md`. Los cinco HTML que traen paleta coinciden sin conflictos, y el ticket usa los mismos hex escritos en línea. La prosa de `DESIGN.md` cita otros valores (teal `#0D9488`, coral `#EF4444`, ámbar `#F59E0B`, éxito `#10B981`) que los HTML no usan y que **fallan AA con texto blanco** (3,74, 3,76 y 2,15). Se descartan, salvo que DEC-11 diga otra cosa.

### Color (tema claro)

Sólo se trasladan a React Native los tokens que usan las pantallas; el resto de la paleta M3 queda fuera.

| Token RN | Hex | Uso |
| --- | --- | --- |
| `primary` | `#00236F` | CTA principal, pestaña activa, títulos de énfasis, enlaces |
| `onPrimary` | `#FFFFFF` | texto sobre `primary` |
| `primaryContainer` | `#1E3A8A` | encabezados y banners navy |
| `primaryFixed` / `onPrimaryFixedVariant` | `#DCE1FF` / `#264191` | chip «Confirmado» |
| `secondary` | `#006A61` | acento teal: filtros activos, estado «abierto», descuentos |
| `onSecondary` | `#FFFFFF` | texto sobre `secondary` |
| `secondaryContainer` / `onSecondaryContainer` | `#86F2E4` / `#006F66` | insignias suaves |
| `secondaryFixed` / `onSecondaryFixedVariant` | `#89F5E7` / `#005049` | chip «Listo para retiro» |
| `tertiaryFixed` / `onTertiaryFixedVariant` | `#FFDDB8` / `#653E00` | chip «Pendiente / En preparación», avisos de plazo |
| `error` / `onError` | `#BA1A1A` / `#FFFFFF` | errores, acciones destructivas |
| `errorContainer` / `onErrorContainer` | `#FFDAD6` / `#93000A` | chip «Cancelado / Expirado», banners de error |
| `surface` | `#FAF8FF` | fondo de pantalla |
| `surfaceContainerLowest` | `#FFFFFF` | tarjetas |
| `surfaceContainerLow` / `surfaceContainer` / `surfaceContainerHigh` | `#F2F3FF` / `#EAEDFF` / `#E2E7FF` | secciones, chips por defecto, campos y chip «Entregado» |
| `onSurface` | `#131B2E` | texto principal |
| `onSurfaceVariant` | `#444651` | texto secundario y metadatos |
| `outline` | `#757682` | borde de campos y controles (4,5:1) |
| `outlineVariant` | `#C5C5D3` | **sólo** divisores decorativos (1,71:1, insuficiente para controles) |

### Contraste medido (WCAG 2.x, cálculo de luminancia relativa)

| Par | Ratio | Nivel |
| --- | --- | --- |
| `onPrimary` / `primary` | 14,29 | AAA |
| blanco / `primaryContainer` | 10,36 | AAA |
| blanco / `secondary` | 6,49 | AA |
| `onSurface` / `surface` | 16,29 | AAA |
| `onSurfaceVariant` / `surface` · / `surfaceContainer` | 8,90 · 8,06 | AAA |
| `error` / blanco | 6,46 | AA |
| chips de estado (los cinco pares de arriba) | 7,23–7,64 | AAA |
| `outline` / blanco | 4,50 | AA y 3:1 para componentes |

**Modo oscuro:** el mockup sólo trae tema claro. **Propuesta:** fijar `userInterfaceStyle: "light"` en la demo y crear la paleta oscura más adelante, previa decisión. Hoy la plantilla está en `automatic`.

### Tipografía

Plus Jakarta Sans con pesos 400/600/700/800. Escala de `DESIGN.md` en px, equivalentes a dp en RN:

| Token | Tamaño / interlineado | Peso | Uso |
| --- | --- | --- | --- |
| `display` | 36/44 | 800 | portada de Explorar (opcional) |
| `headline` | 24/32 | 700 | título de pantalla (versión móvil de `headline-lg`) |
| `title` | 20/28 | 600 | nombre de comercio, total |
| `titleSm` | 18/24 | 600 | título de tarjeta |
| `body` | 16/24 | 400 | texto corrido |
| `bodySm` | 14/20 | 400 | descripciones y metadatos |
| `caption` | 12/16 | 400 | notas al pie |
| `label` | 14/20 | 600 | botones |
| `labelSm` | 12/16 | 600 | chips |
| `overline` | 11/14 | 700 | sólo etiquetas en mayúscula; evitar en texto que deba leerse |

El texto debe respetar el escalado del sistema (`allowFontScaling` activo) y los contenedores tienen que crecer con él. Las tarjetas se verifican al 200 % en T-UI.

### Espacio, forma y elevación

- **Espaciado** (rejilla de 4/8): `xs 4 · sm 8 · md 16 · lg 24 · xl 32`; margen lateral móvil 16; gutter 12.
- **Radios:** controles 12 · tarjetas 16 · hojas inferiores 24 (sólo esquinas superiores) · chips y pastillas 9999.
- **Objetivo táctil:** mínimo **48 dp** en Android. `DESIGN.md` dice 44 px, pero Android recomienda 48 dp y se elige el valor mayor. Botones de 50 dp de alto; campos de 48 dp.
- **Elevación:** nivel 1 en tarjetas (borde 1 dp `surfaceContainerLow` + `elevation: 1`); nivel 2 en barra inferior, encabezado fijo y barra de carrito (`elevation: 4`); nivel 3 en modales y hojas (`elevation: 12` + velo `onSurface` al 40 %). En Android sólo `elevation` controla la sombra: los valores de sombra CSS no se trasladan tal cual.

## 2. Navegación (Expo Router, `frontend/src/app/`)

```text
_layout.tsx                 raíz: fuentes, tema, proveedores; redirige según la sesión
(auth)/                     UI-10 · LUI-07: ingresar, registro, recuperar
(cliente)/_layout.tsx       barra de 4 pestañas: SOLO rol cliente
  (tabs)/explorar/index     UI-01
  (tabs)/comparar/index     UI-02
  (tabs)/carritos/index     UI-04 · insignia = n.º de carritos activos
  (tabs)/pedidos/index      UI-06A · En curso | Historial
  comercio/[comercioId]     tienda (falta en Stitch, MK-01)
  producto/[productoId]     UI-03 (falta en Stitch, MK-01)
  checkout/[carritoId]      UI-05 · modal o pila; al confirmar, reemplaza la ruta (no se puede volver al checkout)
  pedido/[pedidoId]/ticket  UI-06B
  cuenta, notificaciones    icono del encabezado; destino según DEC-20
(comercio)/                 UI-07/08 · LUI-08, sólo con membresía de comercio
(admin)/                    UI-09 · LUI-09, alcance según DEC-10/13
```

Reglas: tras confirmar, el checkout navega con `replace` al pedido y el botón Atrás nunca reenvía la compra. Cada pestaña conserva su propia pila y su scroll. Los grupos `(comercio)` y `(admin)` sólo se montan si el rol lo permite; esto es una **comodidad de interfaz**, y la seguridad real vive en RLS (BE-01). El enlace profundo usa el esquema `paseoya://`, ya configurado en `app.json`.

## 3. Componentes

| Componente | Variantes y estados | Pantallas |
| --- | --- | --- |
| `AppHeader` | logo + plaza + título; acciones campana y cuenta; con botón Atrás en pilas | todas |
| `TabBar` | 4 pestañas con icono y etiqueta; insignia de conteo; activa con `primary` | cliente |
| `Button` | `primary` · `secondary` · `outline` · `ghost` · `destructive`; `loading` (bloquea el doble toque), `disabled` | todas |
| `Chip` | `filter` (con selección) · `status` (5 tonos de estado) · `info` | 01, 02, 04, 06 |
| `StoreCard` | foto 16:9, abierto/cerrado, local/piso, tiempo de retiro marcado como «estimado», CTA | 01 |
| `ProductCard` | foto 1:1, precio, precio anterior, stock (`disponible` · `últimas` · `agotado`), CTA del comercio | 01, 02, tienda |
| `OfferBadge` | % de descuento; mostrar precio anterior sólo si existe | 01, 02 |
| `ComparisonRow` | comercio + producto + precio + stock + retiro; sin la marca «equivalente» hasta DEC-09 | 02 |
| `CartCard` | por comercio: líneas, `QuantityStepper`, subtotal, `ExpiryTimer`, CTA de checkout | 04 |
| `QuantityStepper` | −/+ de 48 dp, límite según stock, eliminar en 0 con confirmación | 03, 04 |
| `ExpiryTimer` | cuenta regresiva accesible (el lector anuncia minutos, no cada segundo); vencido | 04, 05, 06 |
| `PriceText` | formato `es-BO` en bolivianos; un solo formateador para toda la app | todas |
| `PaymentMethodSelector` | radios excluyentes «QR (simulado)» / «Efectivo al retirar», con condiciones | 05 |
| `OrderCard` | comercio, `Chip` de estado, importe, método, límite, acción priorizada | 06A |
| `PickupCredential` | QR + PIN; oculto si el estado no lo permite; marca «ilustrativo» en fixtures | 06B |
| `LocationBlock` | local, piso, indicaciones; el mapa queda pendiente de DEC-20 | 05, 06B |
| `EmptyState` · `ErrorState` · `OfflineBanner` · `Skeleton` | mensaje, acción de recuperación y reintento | todas (MK-02) |
| `ConfirmSheet` | hoja inferior para confirmar acciones que tienen efecto | 04, 05, 06 |

## 4. Matriz vista → componentes → estados → acciones

| Vista | Componentes | Estados obligatorios | Acciones y destino | RF |
| --- | --- | --- | --- | --- |
| UI-01 Explorar | Header, banner, carrusel de categorías (`Chip`), `StoreCard`, `ProductCard`/`OfferBadge` | cargando (skeleton) · sin red · error · sin ofertas · comercio cerrado · agotado | búsqueda → Comparar; tienda → `comercio/[id]`; oferta → `producto/[id]`; «Añadir» → carrito **de ese comercio** + aviso | 05–09, 12 |
| UI-02 Comparar | campo de búsqueda con limpiar, `Chip` de filtros, resumen, `ComparisonRow` | sin consulta · sin resultados · filtro sin datos · stock desactualizado · cargando | «Agregar a carrito [comercio]» → ese carrito; fila → producto | 09–12 |
| UI-03 Detalle *(nueva)* | galería, `PriceText`, stock, `QuantityStepper`, comercio | stock cambió · agotado · error | añadir al carrito del comercio; ver tienda | 11–13 |
| UI-04 Carritos | `CartCard` ×n, `ExpiryTimer`, bloque explicativo del flujo | vacío · por vencer · vencido · precio/stock cambió · error al actualizar | modificar cantidad; eliminar línea o carrito; «Ir a pagar» → `checkout/[carritoId]` | 13–17 |
| UI-05 Checkout | resumen, `LocationBlock`, `PaymentMethodSelector`, protocolo de retiro, `Button` con loading | procesando · rechazo por stock · error con reintento **idempotente** · carrito vencido · fuera de horario | confirmar → `replace` a pedido; «Modificar carrito» → Atrás | 18–22 |
| UI-06A Pedidos | pestañas En curso/Historial, `OrderCard`, `Chip` de estado | vacío por pestaña · cargando · error · cada estado del pedido (§5) | ver código de retiro (sólo si `READY_FOR_PICKUP`); detalle; acciones extra según DEC-20 | 23–26 |
| UI-06B Ticket | `PickupCredential`, productos, total, `LocationBlock`, aviso de seguridad | no listo · listo · entregado/usado · vencido · cancelado · sin conexión (vista en caché, marcada) | guardar / descargar / reportar sólo si DEC-20 las aprueba | 22–26 |
| UI-10 Cuenta *(nueva)* | formularios con error en línea | credenciales inválidas · sesión vencida · recuperación | ingresar → área según rol | 01–04 |

## 5. Estados del pedido y del pago en la interfaz

Se usan los estados **propuestos** en SRC-02 §12–13. Pedido y pago son dos chips separados y nunca se mezclan en un mismo texto.

| Pedido (SRC-02) | Etiqueta propuesta | Tono | ¿Credencial visible? |
| --- | --- | --- | --- |
| `CREATED` / `CONFIRMED` | Confirmado | `primaryFixed` | no |
| `IN_PREPARATION` | En preparación | `tertiaryFixed` | no |
| `READY_FOR_PICKUP` | Listo para retiro | `secondaryFixed` | **sí** (QR + PIN según DEC-16) |
| `DELIVERED` | Entregado | `surfaceContainerHigh` | no (marcado como usado) |
| `CANCELLED` / `EXPIRED` | Cancelado / Expirado | `errorContainer` | no |

| Pago | Etiqueta | Nota |
| --- | --- | --- |
| `PENDING` | QR pendiente (simulado) · Efectivo al retirar | nunca «Pagado» antes de la confirmación simulada (DEC-04) |
| `PAID` | Pago QR simulado confirmado · Efectivo cobrado | el mockup dice «100 % pagado»: se reemplaza para no sugerir un cobro real |
| `REFUNDED` | Reembolso simulado | RN-08 |

## 6. Textos y formato

- **Idioma:** español de Bolivia con **trato formal (usted)**, decidido en DEC-11. Se prefieren formas neutras («Agregar al carrito», «Ver código de retiro»); cuando haga falta un verbo dirigido, va en usted («Confirme su pedido», «Presente este código en el local»). Nunca tuteo.
- **Moneda:** el formateador único es `Intl.NumberFormat('es-BO', { style: 'currency', currency: 'BOB' })`. La salida exacta (`Bs`, separadores) se verifica en el dispositivo durante LUI-02 antes de fijar los textos.
- **Glosario obligatorio:**
  - «QR de pago (simulado)» y «Código de retiro» nunca comparten nombre ni icono (MK-04).
  - «Tiempo estimado» va siempre etiquetado como estimado.
  - Los plazos se escriben como **[plazo DEC-06]** hasta que se decidan (MK-05).
- **Frases prohibidas hasta su decisión:**
  - «stock reservado» (DEC-05).
  - «pagado» para un QR simulado sin confirmar (DEC-04).
  - «equivalente» en la comparación (DEC-09).
  - «3 días hábiles» y «72 horas» (DEC-06).

**Notas de implementación (LUI-02):**
- `String.prototype.normalize('NFD')` no descompone las tildes en Hermes/Android; la búsqueda usa un mapa explícito (`normalizeSearch`).
- Las etiquetas de las pestañas necesitan `labelVisibilityMode="labeled"` en cada `NativeTabs.Trigger`; en la raíz no tuvo efecto.
- Sin librería de iconos en JS, las acciones del encabezado son texto («Avisos», «Cuenta»).
- Con React Compiler, `ref.current++` devolvió el valor ya incrementado; se usa asignación explícita.
- Expo Router 57 tipa la ruta índice de una carpeta dinámica como `/…/index` y no la resuelve al navegar; se usan rutas con nombre (`pedido/[pedidoId]/detalle`).

## 7. Fixtures coherentes (datos ficticios, resuelve MK-06)

Son datos sintéticos para LUI-02–06. Los nombres de tienda salen del mockup y son ficticios. **Fijan un único local por comercio**, en lugar del 208/204 de TechZone. Todas las pantallas leen del mismo módulo de fixtures, así que una cifra no puede diferir entre vistas.

| Comercio | Local / piso | Categoría | Estado |
| --- | --- | --- | --- |
| `com-techzone` TechZone | Local 208 · Planta baja | Tecnología | abierto |
| `com-moda` Boutique Aranjuez | Local 105 · Piso 1 | Moda | abierto |
| `com-cafe` Café del Paseo | Local 012 · Planta baja | Gastronomía | cerrado (sirve para probar el estado «cerrado») |

| Caso | Contenido |
| --- | --- |
| Productos | 3 por comercio; en TechZone, un producto con stock 1 (últimas unidades) y otro agotado; un producto con precio anterior |
| Carritos | 2 activos (TechZone y Boutique) con distinto tiempo restante, más 1 vencido para su estado |
| Pedidos | uno por cada estado de §5, con QR simulado y con efectivo; totales calculados desde sus líneas, nunca escritos a mano |
| Credenciales | PIN `000000` y un QR con el texto `FIXTURE-NO-VALIDO`, visibles con la marca «ilustrativo»; nunca un formato que el backend acepte |

## 8. Recursos y licencias (MK-07)

| Recurso | Origen en Stitch | Propuesta para RN | Estado |
| --- | --- | --- | --- |
| Plus Jakarta Sans | Google Fonts CDN | paquete `@expo-google-fonts/plus-jakarta-sans`, empaquetado en la app | licencia SIL OFL 1.1, uso libre; se instala en LUI-02 |
| Iconos | Material Symbols vía CDN | `@expo/vector-icons` (MaterialIcons/MaterialCommunityIcons, ya incluido en Expo) | Apache 2.0; los nombres se mapean en LUI-02 |
| Fotos de tiendas y productos | `lh3.googleusercontent.com` (generadas por Stitch) | **placeholders locales sin marca** (bloques de color con icono de categoría) | DEC-15: no se usan las fotos de Stitch; datos 100 % ficticios |
| Logo PaseoYa | `logo.html` / `logo.png` | **texto provisional** «PaseoYA» con Plus Jakarta Sans 800 y color `primary` | DEC-11: provisional hasta que Usuario aporte un logo |
| Mapa de la plaza | imagen remota | fuera hasta DEC-20 | — |
| Tailwind CDN | HTML | no aplica a RN; los tokens se trasladan a `src/constants/theme.ts` | — |

## 9. Propuesta para MK-01–08

| ID | Propuesta del agente | Espera |
| --- | --- | --- |
| MK-01 | Detalle, tienda y cuenta se diseñan con los componentes de §3 y las rutas de §2; comercio y admin, en LUI-08/09 | DEC-10/13 |
| MK-02 | Estados de §4 obligatorios en cada vista; T-UI los recorre con fixtures | — |
| MK-03 | El texto del carrito dice «Disponible ahora» sin prometer reserva | DEC-05 |
| MK-04 | Glosario de §6; chips de pago separados del pedido | DEC-04 |
| MK-05 | Marcador **[plazo DEC-06]** en todos los textos de plazo | DEC-06 |
| MK-06 | **Resuelto** (§7): TechZone = Local 208 · Planta baja | confirmado por Usuario el 2026-10-03 |
| MK-07 | Tabla de §8; las fotos de Stitch quedan fuera | DEC-11/15 |
| MK-08 | La comparación muestra «productos similares de varios comercios» sin afirmar equivalencia | DEC-09 |

## 10. Cierre de LUI-01 (respuesta a DEC-11)

Respuesta de Usuario del 2026-10-03: aprobados los puntos 1, 2, 3 y 6; punto 4 → texto provisional; punto 5 → **usted** con el glosario; punto 7 → **Local 208 · Planta baja**; punto 8 → placeholders sin marca. Lista original:

1. La paleta canónica Material 3 de §1, descartando los hex de la prosa.
2. El tema claro sólo para la demo.
3. Plus Jakarta Sans y los iconos Material.
4. El logo.
5. El tuteo y el glosario de §6.
6. Las cuatro pestañas y las rutas de §2.
7. TechZone = Local 208.
8. Sustituir las fotos de Stitch (DEC-15).

**Evidencia:**
- Análisis estático de los 8 HTML, `DESIGN.md` y las capturas: EVID-LUI-01a en [[05-Desarrollo/Testing]].
- La comparación visual en dispositivo llegará con la implementación de LUI-02: `NO_EJECUTADA`.
