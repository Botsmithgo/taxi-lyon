# Taxi Montdor — Project Context

## What This Is
A single-page marketing/booking website for **Taxi Montdor**, a professional taxi service based in Lyon, France. Built for a friend (the taxi driver). The site covers three service lines: professional/private transport, long-distance & airports, and CPAM-covered medical transport.

**Live URL:** https://botsmithgo.github.io/taxi-lyon  
**GitHub repo:** https://github.com/Botsmithgo/taxi-lyon  

---

## Business Info

| Field | Value |
|---|---|
| Business name | Taxi Montdor |
| Phone | 06 99 83 53 89 / +33699835389 |
| Email | taxi.montdor@gmail.com |
| Address | 43 Rte de Limonest, 69380 Lissieu, France |
| Hours | 7j/7 — 24h/24 |
| Drivers | Sullivan, Gabriel |
| WhatsApp | https://wa.me/33699835389 |

---

## Tech Stack

- **Single HTML file** — all CSS and JS inline in `index.html`. No build tools, no frameworks.
- **Hosting** — GitHub Pages via `.github/workflows/pages.yml`
- **Form backend** — Formspree (endpoint needs updating — see Pending below)
- **Images** — local JPEGs in project root (compressed from original PNGs using macOS `sips`)

---

## Files

| File | Purpose |
|---|---|
| `index.html` | The entire site — HTML, CSS, JS all inline |
| `tesla-hero.jpg` | Hero section background (Tesla taxi on Lyon street with Fourvière) |
| `lyon-aerial.jpg` | Zone section image (Lyon aerial shot) |
| `man-in-car.jpg` | Service card — Transport professionnel & privé |
| `outdoors.jpg` | Service card — Longue distance & aéroports (Alpine/outdoors photo) |
| `indexbackup.html` | Backup of an earlier version |
| `backup-longdistance-photo.txt` | Unsplash URL backup for original long-distance card photo |
| `tesla-hero.png` | Original uncompressed hero PNG (kept as source) |

---

## Features Built

- **Hero** — Tesla photo background, phone popover (Appeler / Envoyer un SMS), badges row, hero card with float animation
- **Trust bar** — 4 items (Ponctualité, CPAM, Tarifs, Discrétion)
- **Services** — 3 cards with local images and zoom-on-hover
- **CPAM section** — 3-step explainer on dark blue gradient bg
- **Zone** — Lyon aerial photo + city list
- **Why Us** — 6 cards
- **Testimonials** — 3 reviews (Sophie K., Marie C. / Sullivan, Thomas M. / Gabriel)
- **FAQ** — 8 items with smooth CSS accordion (grid-rows trick)
- **Contact** — Formspree form + phone/WhatsApp/address info cards
- **Footer** — links, address, hours
- **Sticky mobile bar** — Appeler / WhatsApp / Devis

### Phone UX
Every phone number on the site (nav, CPAM inline, contact card, footer, mobile bar) opens a **global action sheet** with two options: Appeler and Envoyer un SMS. Implemented as a single shared sheet (`#gsheet-wrap`) triggered by `[data-phone-trigger]` attributes. Desktop shows a centered card, mobile shows a bottom sheet.

### Animations
Full scroll-reveal system using IntersectionObserver:
- `.reveal` — fade up
- `.reveal-left` / `.reveal-right` — slide in from sides
- `.reveal-scale` — scale + fade up
- `.reveal-stagger` — parent wrapper, nth-child delays 0–400ms
- Hero: load-triggered rise animation (not scroll)
- Hero card: infinite float loop
- CPAM step numbers: stamp animation on scroll entry
- CPAM background: slow gradient pulse
- FAQ: smooth open/close via `grid-template-rows: 0fr → 1fr`
- Service cards: image zoom on hover
- Nav links: sliding underline on hover
- Hero parallax: desktop only, `requestAnimationFrame`
- All wrapped in `@media (prefers-reduced-motion: no-preference)`

### Form Success State
After submit, the form fades out and a success card animates in with a checkmark, confirmation message, and phone number. Uses `fetch()` — no page redirect.

---

## Pending / To Do

### ⚠️ Formspree — NEEDS ACTION
The form currently uses the legacy endpoint `https://formspree.io/taxi.montdor@gmail.com` which is deprecated and causes errors on submit.

**Fix:**
1. Log in at formspree.io (account: taxi.montdor@gmail.com)
2. Verify the email address (confirmation email was sent)
3. Create a new form in the dashboard
4. Copy the endpoint — format: `https://formspree.io/f/XXXXXXXX`
5. ✅ Done — endpoint is `https://formspree.io/f/mkokgnwd`

### Future v2 ideas
- Mentions légales + Politique de confidentialité pages
- Google Reviews integration
- Online booking calendar
- Custom domain (client to purchase)

---

## Deployment

Push to `main` branch → GitHub Actions deploys automatically to GitHub Pages.

```bash
git add index.html
git commit -m "your message"
git push origin main
```

Pages URL updates within ~1 minute.

---

## CSS Variables (quick reference)

```
--bleu: #0B3D6F       (primary navy)
--cyan: #4FB3E8       (accent blue)
--vert: #10B981       (green / CTA)
--or:   #F5B84C       (gold / stars)
--ink:  #0C1B2E       (body text)
--ink-2: #334966      (secondary text)
--ink-3: #6B7F98      (muted text)
```
