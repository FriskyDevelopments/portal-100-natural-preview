# Sistema de diseño · Portal 100% Natural

Nota corta para quien edite la página. Los valores viven como variables `--na-*` en [`assets/polish.css`](../assets/polish.css).

## Principios
1. **Una tarea por pantalla.** Cada paso tiene una acción principal (verde bosque) y, como mucho, una secundaria (borde).
2. **El ticket es el héroe.** El ticket y el comprobante con QR son la ilustración; no agregues fotos de stock.
3. **El movimiento explica, no decora.** Solo `transform` y `opacity`, curva `--na-ease`, y siempre con estado final legible si hay movimiento reducido.
4. **Honestidad.** Es una vista previa: no se agregan sellos, certificados ni testimonios falsos.

## Color
| Token | Valor | Uso |
| --- | --- | --- |
| `--na-bosque` | `#14532D` | Nav, pie, botón primario |
| `--na-hoja` | `#2E7D4F` | Enlaces, bordes activos, foco de campos |
| `--na-brote` | `#6BAE5F` | Acentos y degradados |
| `--na-sol` | `#F2C14E` | CTA "Entrar", puntos, anillo de foco |
| `--na-tinta` | `#1B3B2A` | Texto |
| `--na-tinta-suave` | `rgba(27,59,42,.74)` | Texto secundario (mínimo; no bajar la opacidad) |
| `--na-crema` | `#FFFDF6` | Tarjetas |
| `--na-arena` | `#EFEADC` | Fondo |

Contraste mínimo 4.5:1 en texto normal. Sobre verde, el crema no baja de 0.8 de opacidad.

## Tipografía
- **Outfit** (400–700): titulares, botones, etiquetas. Interletrado negativo en titulares grandes (−0.03 a −0.05em).
- **Nunito Sans** (400/600): texto corrido. 16–18px, interlineado 1.6.
- **Cormorant Garamond** (500): solo la firma "FOLIOS." No usar en otro lado.
- Escala fluida: `--na-step--1` … `--na-step-2` y `--na-step-hero` (`clamp(2.6rem, …, 4.75rem)`). En móvil el héroe usa `clamp(2.75rem, 12.5vw, 3.6rem)`.
- `text-wrap: balance` en titulares y `pretty` en párrafos.

## Espaciado y forma
- Base de 4px: `--na-space-1` (4) … `--na-space-8` (64). Margen lateral fluido `--na-gutter` (18–44px).
- Radios: campos 12px, tarjetas chicas 16px, tarjeta principal 26px, cápsulas 999px.
- Sombra de tarjeta principal: `--na-shadow-card`.

## Movimiento
- Curva única `--na-ease` = `cubic-bezier(0.16, 1, 0.3, 1)`; rápido 180ms, normal 320ms.
- Entradas del héroe escalonadas (ya en la plantilla), tarjetas de preguntas con elevación al pasar y revelado con `animation-timeline: view()` donde exista.
- `prefers-reduced-motion: reduce` anula animaciones y transiciones de forma global.

## Accesibilidad
- Foco visible: anillo `--na-sol` de 3px (crema sobre nav y pie); los campos usan borde `--na-hoja` + halo, y conservan un `outline` transparente para que el foco se vea en modo de contraste forzado.
- Todo lo que se pulsa es `<button>` o `<a>`. Los botones de solo ícono llevan `aria-label` o texto oculto.
- Mensajes que cambian solos (validación del folio) llevan `aria-live="polite"`.
- Probar con Tab de principio a fin y con Lighthouse antes de fusionar.

## Cómo sobrescribir un estilo de la plantilla
La plantilla usa estilos en línea y un bloque `<style>` propio. Desde `polish.css`, apunta al gancho `data-na` con `html [data-na="..."]` y `!important` solo cuando compitas con un estilo en línea.
