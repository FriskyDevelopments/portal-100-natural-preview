# Changelog

Formato basado en [Keep a Changelog](https://keepachangelog.com/es-ES/1.1.0/). Fechas en America/Monterrey.

## [1.1.0] · 2026-11-16 — Pulido "nivel premio"

### Agregado
- `<head>` completo: `lang="es-MX"`, título y descripción reales, `canonical`, Open Graph y Twitter Card con imagen 1200×630 (`assets/img/og-card.jpg`), JSON-LD `WebApplication`, `theme-color`.
- Set de íconos: `favicon.ico`, `favicon.svg`, `apple-touch-icon.png`, íconos 192/512 y `site.webmanifest`.
- `404.html` con la marca, `robots.txt` y `sitemap.xml`.
- `assets/polish.css`: tokens de color, tipografía fluida, espaciado, radios y movimiento; foco visible en todos los controles; cápsula de vidrio en la navegación; elevación de tarjetas; revelado al hacer scroll como mejora progresiva.
- Shell estático de arranque (`#na-shell`) para pintar al instante mientras carga el runtime, enlace "Saltar al contenido" y `<noscript>` con contacto.
- `docs/DESIGN-SYSTEM.md`.

### Cambiado
- React 18.3.1 y las tres fuentes se sirven desde el propio sitio (sin unpkg ni Google Fonts en tiempo de carga). Mismos archivos: el hash SRI coincide.
- `support.js` y `qr.js` cargan con `defer`; ya no bloquean el render.
- Logos en WebP al doble de su tamaño de uso, con `width`/`height` (sin saltos de layout).
- Contraste: texto secundario sube a ≥ 4.5:1 sobre crema, arena y verde.
- Navegación: los enlaces ahora son `<button>` (teclado y lector de pantalla); `<nav>`, `role="banner"`, `role="main"` y `role="contentinfo"`.
- Botones de solo ícono con nombre accesible; el aviso del folio se anuncia (`aria-live`); el correo usa `type="email"` y `autocomplete`.
- Tipografía del héroe fluida (`clamp`) y más grande en móvil; botón de Fausto más compacto en pantallas chicas.
- `prefers-reduced-motion`: todas las animaciones quedan en su estado final.

### Quitado
- `image-slot.js` (65 KB que no se usaban en la página).

### Medido (Lighthouse 12, servidor local con gzip, mediana de 3)
| | Rendimiento | Accesibilidad | Buenas prácticas | SEO |
| --- | --- | --- | --- | --- |
| Móvil antes → después | 85 → 94 | 85 → 100 | 96 → 100 | 91 → 100 |
| Escritorio antes → después | 99 → 100 | 85 → 100 | 96 → 100 | 91 → 100 |

## [1.0.1] · 2026-11-16
- Dominio propio `factura100.folios.works` (`CNAME`). PR #3.

## [1.0.0] · 2026-09
- Vista previa inicial del portal de autofactura.
