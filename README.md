<p align="center">
  <img src="na-logo.png" alt="100% Natural" width="240">
</p>

<h1 align="center">Portal 100% Natural · vista previa de diseño</h1>

<p align="center"><b>Vista previa estática del portal de autofactura de 100% Natural</b></p>

<p align="center">
  <img src="https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white" alt="HTML5">
  <img src="https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black" alt="JavaScript">
</p>

Vista previa estática, en una sola página, del diseño del **portal de autofactura de 100% Natural**. Está pensada para que el comercio, ventas y operación revisen el flujo antes de construir el producto. El cliente escanea el QR de su ticket, captura sus datos fiscales y recibe su factura ("Tu factura, en dos pasos"). La página muestra ese flujo con la paleta de palmeras y verdes de la marca, un generador de QR del lado del cliente y la sección de preguntas frecuentes. Es **solo diseño**: no emite ni timbra facturas. La guía del paquete promocional está en [`docs/PROMO-PACKAGE-IMPLEMENTATION-GUIDE.md`](docs/PROMO-PACKAGE-IMPLEMENTATION-GUIDE.md).

## Arquitectura

```mermaid
flowchart LR
  cliente([Cliente con ticket]) -->|escanea QR| page[index.html<br/>portal de autofactura · diseño]
  page --> qr[qr.js<br/>qrcode-generator]
  page --> slots[image-slot.js<br/>marcadores de imagen]
  page --> rt[support.js<br/>runtime generado]
  page --> assets[/na-logo · na-hero · na-ticket · palmeras SVG/]
  page -.->|sin backend| nota[No timbra ni envía datos]
  repo[(main /)] -->|GitHub Pages| page
```

## Stack

- HTML y CSS estáticos, sin paso de build
- JavaScript: `qr.js` (qrcode-generator 1.4.4, minificado), `support.js` (runtime generado) e `image-slot.js`
- Recursos de marca en PNG y SVG (logos, héroe, ticket y palmeras)

## Estructura del proyecto

```text
index.html          página de vista previa
support.js  qr.js  image-slot.js
na-logo.png  na-logo-tinta.png  na-hero.png  na-ticket.png  na-palmera.png
palmera-*.svg       palmeras (bosque, crema, pizarra, verde)
docs/PROMO-PACKAGE-IMPLEMENTATION-GUIDE.md
```

## Desarrollo local

No hay dependencias ni scripts. Basta con servir la carpeta de forma local.

```bash
# Luego abre http://localhost:8000
python3 -m http.server 8000
```

## Despliegue

GitHub Pages publica la rama `main` (raíz) en https://friskydevelopments.github.io/portal-100-natural-preview/.
