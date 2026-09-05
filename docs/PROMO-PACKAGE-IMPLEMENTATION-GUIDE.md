# Implementation guide — Promo package for Portal Facturación 100% Natural

**Audience:** Hostinger Backend, ops, and anyone shipping the merchant-facing autofactura portal for **100% Natural** (Red Hosted + Hostinger).  
**Product UI (locked):** Claude design **Portal 100 Natural** — not the Folios marketing site, not the old workers.dev green/orange DEMO.  
**Preview:** https://friskydevelopments.github.io/portal-100-natural-preview/  
**Repos:** `FriskyDevelopments/portal-100-natural-preview` (static) · product app `FriskyDevelopments/folios-portal`  
**Design source:** `/workspace/kb/claude-design/Portal 100 Natural.dc.html` (+ logos/palmeras/screens)

---

## 1. Goal of the promo package

Give 100% Natural (and Red Hosted / Hostinger sales) a **ready-to-run kit** to:

1. Point customers at the autofactura portal with one clear URL.  
2. Explain the flow in kitchen Spanish (“Tu factura, en dos pasos”).  
3. Drive QR / ticket → portal → datos fiscales → factura lista.  
4. Stay on-brand (palmera / natural greens) and **never** claim a demo timbra if it doesn’t.

**Out of scope for v1 promo:** Casa Barra Vieja guest site, Folios SaaS landing, Open Stay Pass wallets (separate Hostinger secrets track).

---

## 2. Brand & copy guardrails

### Visual (from Portal 100 Natural)

| Role | Notes |
|------|--------|
| Palette | Deep forest greens (`#061A0F`–`#1B5E37`), lime accents (`#A7C957` / `#C7E86B`), warm ticket oranges, cream paper (`#E4DFCF`) |
| Marks | `na-logo.png` / `na-logo-tinta.png`, palmera SVGs, `na-hero.png`, `na-ticket.png` |
| Tone | Mobile-first, large type, two CTAs max on hero |
| Language | Spanish (MX). Kitchen language, not SAT jargon on the hero |

### Do

- Lead with **QR de la tira / ticket** → portal.  
- Stamp demos: **“la demo no timbra”** until PAC/timbrado is live on that host.  
- Separate **SAT/timbrado** language from marketing “promo” language.

### Don’t

- Ship Folios ink/lime marketing look as if it were 100% Natural.  
- Use the rejected workers.dev DEMO page as the promo screenshot.  
- Mix HostCasa gold/navy into this pack.  
- Promise auto-deploy from “approved PR” as a Hostinger feature — Hostinger Git deploys on **push to the connected branch** (use required reviews → merge to `main`).

---

## 3. Package contents (deliverables)

Create a folder (suggested): `promo-100-natural-factura/`

```
promo-100-natural-factura/
  README.md                 # this pack’s short operator sheet
  01-one-pager.md           # Spanish one-pager (print + WhatsApp)
  02-qr-kit/                # PNG/SVG QR → portal URL + ticket mock
  03-social/                # 1080² + story crops from na-hero / na-ticket
  04-email-sms/             # short templates (magic link / “ya es tuya”)
  05-in-store/              # counter card + sticker specs
  06-portal-checklist.md    # go-live + Hostinger Git
  assets/                   # logos + palmeras (copied from portal preview)
```

### Minimum viable pack (ship first)

1. **Canonical URL** (pick one and lock it):  
   - Preferred brand: `factura.100natural.mx` or `autofactura.100natural.mx`  
   - Folios lane fallback: `100natural.folios.works`  
2. **One-pager** (½ page): problem → two pasos → QR → soporte.  
3. **QR** pointing at that URL (UTM: `utm_source=tira&utm_medium=qr&utm_campaign=100n_factura`).  
4. **3 screenshots** from the Claude portal only (hero, datos fiscales, “Lista. Ya es tuya”).  
5. **Disclaimer** line for all creative: demo vs producción timbrada.

---

## 4. Implementation steps

### Phase A — Freeze the story (½ day)

1. Confirm merchant legal name / RFC display name for 100% Natural.  
2. Lock portal URL + Hostinger site (shared hosting, **static**).  
3. Confirm whether promo drives to **preview** (GitHub Pages) or **production Hostinger** — never mix in the same QR.  
4. Write the three hero lines (already in design):  
   - “Tu factura, en dos pasos.”  
   - “Apunta al QR de tu tira.”  
   - “Lista. Ya es tuya.”

### Phase B — Build creative from approved assets (1 day)

1. Copy logos/palmeras from `portal-100-natural-preview/` into `assets/`.  
2. Export social crops; keep ticket orange + forest green.  
3. Generate QR (high contrast, quiet zone ≥ 4 modules).  
4. Optional: adapt `Promo Referidos.dc.html` only if referidos is in scope; otherwise skip.

### Phase C — Hostinger hosting for the portal (Backend)

1. hPanel → website → **Deploy as static** (no `package.json` required).  
2. **Advanced → Git** → Hostinger GitHub App → `FriskyDevelopments/portal-100-natural-preview` → branch **`main`**.  
3. First Deploy; confirm Auto-deployment chip.  
4. GitHub branch protection on `main`: required reviews + CI; merge = Hostinger pull.  
5. Custom domain + SSL; clear cache after first DNS.  
6. **Do not** use archive MCP deploy for ongoing promo if Git is connected — one source of truth.

**PR checks:** add a lightweight GitHub Action that validates `index.html` exists and assets are present; Hostinger does not run PR preview deploys natively.

### Phase D — Wire promo → portal (½ day)

1. Print/digital QR → production URL.  
2. UTM + optional short link.  
3. In-store card: logo + QR + “Escanea tu tira”.  
4. WhatsApp blast template (short): link + “dos pasos” + hours of support.

### Phase E — Launch checklist

- [ ] Portal loads on phone over LTE (CDN/unpkg reachable if used).  
- [ ] QR deep-links to hero, not a 404.  
- [ ] Demo stamp visible if not timbrando.  
- [ ] Privacy / datos fiscales copy matches Aviso Privacidad Folios if shared stack.  
- [ ] Hostinger Backend owns env/secrets if/when Node API is added later (static pack needs none).  
- [ ] Promo assets version-tagged (`v1.0-100n-factura`) in the promo repo or Drive.

---

## 5. Roles

| Role | Owns |
|------|------|
| **FR!sky / product** | Story lock, Claude UI fidelity, promo copy |
| **Hostinger Backend** | Site on Hostinger, Git auto-deploy, domain/SSL, later Node/API if any |
| **100% Natural / Red Hosted** | In-store print, WhatsApp, staff training |
| **Folios** | Timbrado/PAC when production leaves demo |

---

## 6. Suggested one-pager skeleton (ES)

**Título:** Factura 100% Natural — en dos pasos  
**Sub:** Escanea el QR de tu tira y listo.  
**Paso 1:** Apunta al QR / abre el enlace.  
**Paso 2:** Confirma tus datos fiscales.  
**Resultado:** Descarga o guarda tu factura.  
**Soporte:** [WhatsApp / horario]  
**Pie:** Portal operado con Folios · [URL] · [demo no timbra / timbrado SAT según entorno]

---

## 7. Success metrics (first 14 days)

- QR scans / unique portal sessions  
- Completions past “datos fiscales”  
- Support tickets (“no abre el QR”, “no llega el correo”)  
- Zero wrong-URL incidents (preview vs prod)

---

## 8. References

- Live preview: https://friskydevelopments.github.io/portal-100-natural-preview/  
- Preview repo: https://github.com/FriskyDevelopments/portal-100-natural-preview  
- Product repo: https://github.com/FriskyDevelopments/folios-portal  
- Hostinger Git (static): hPanel → Advanced → Git  
- Design: `Portal 100 Natural.dc.html`, `Firma Contrato 100 Natural.dc.html`

---

*Guide version: 2026-09-05 · FR!sky*
