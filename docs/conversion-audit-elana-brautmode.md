# Conversion audit: elana-brautmode.de

**Date:** 19 August 2026  
**Live URL:** https://elana-brautmode.de  
**Framework:** “Why the Best-Looking Websites Don't Sell” (Luke / Brave Brand) — aesthetic narcissism vs. a clarity-first conversion engine  
**Webflow site:** Elana Brautmode 2025 (`68f144e9150839c5cf340319`)  
**Pages sampled:** Homepage `/`, booking `/termin`, FAQ `/faq/budget-kauf`  
**Method:** Live HTML + published copy, Webflow Designer tree, custom-code inspection. PageSpeed Insights and CrUX were unavailable (HTTP 429 / 403).

This is **not** the old cinematic clone in `elana_clone/`. The live site is already a later, conversion-oriented rebuild. The remaining issues are leftover cinema, English UI, CTA hierarchy, and a few token-burning extras — not Spline/GSAP/scrolljacking.

**Publish status:** Designer copy edits from this audit are **unpublished**. The live site still shows the old hero italic and English search/newsletter chrome until someone publishes in Webflow.

---

## Executive scorecard

| Category | Pass criteria | Live verdict | Notes |
| :--- | :--- | :---: | :--- |
| **1. 3-Second Clarity** | H1, location/service, and primary CTA immediately legible without scrolling | **PASS with caveats** | H1 “Finde dein Brautkleid in Gaggenau”, 5,0 ★, CTA “Privaten Brauttermin anfragen”. Caveats: cinematic italic, nav “Kontakt” instead of a high-contrast action, Du/Sie mix. |
| **2. Native Scroll** | 100% natural scroll speed, zero scrolljacking, zero horizontal lock-ins | **PASS with caveats** | No GSAP, Lenis, Spline, canvas, or background video. Caveats: hero Webflow slider, Splide autoscroll marquee, dress “ziehe oder wische” track. |
| **3. Content Availability** | No key information hidden behind hover states | **PASS with caveats** | Reviews, process, and dress names are visible. Prices are **not** on the homepage (they appear on `/termin` and `/faq/budget-kauf`: from ~1.200 €). |
| **4. Mobile Speed** | Loads fully in < 2s on 4G; no laggy animations or massive video loops | **MIXED / unmeasured** | No MP4 loops. Local Inter Tight + AVIF LCP preload exist. Still: jQuery, 42 `data-w-id` interactions, 54 `opacity:0` starters, Splide, cookie banner, delayed slider BGs. |
| **5. Outcome Focus** | Every visual element helps the customer decide | **MIXED** | Strong offer/proof/process. Leftover cinema, duplicate review H2s in Designer, decorative Great Vibes, English chrome, leftover ecommerce URLs. |
| **6. Trust & Conversion** | Clear proof, credentials, 1–2 tap CTA flow | **PASS with caveats** | 5,0 ★ / 99 Google reviews, Schneiderin mit Diplom, tel + WhatsApp, `/termin` is a real conversion engine. Caveats on the **live** site: cookie banner, English newsletter chrome, mobile “Kontakt” → `#kontakt`. Designer (unpublished) already retargets that item to `/termin`. |

**Bottom line:** The site already sells better than a Dribbble piece. It fails the video’s test where it still *performs* for the visitor (italic cinema, English UI, weak nav CTA) instead of answering *what / where / why trust / how to get it* in one scan.

---

## Part 1 — Core thesis on this site

| Aesthetic narcissism (trap) | Clarity-first engine (goal) | Elana today |
| :--- | :--- | :--- |
| Treats the visitor like cinema | Respects fast scanning | Homepage H1 is scan-friendly; the hero italic is still a movie line. |
| Scrolljacking & delays | Native scrolling | Native vertical scroll. Soft taxes: slider, Splide marquee, interaction fade-ins. |
| Concealed data on hover | Immediate vital facts | No hover-gated pricing. Homepage still omits price orientation. |
| High latency / bloat | Instant load | No WebGL/video hero. Interaction + Splide + cookie banner still cost tokens. |
| Impresses other designers | Sells to real brides | Copy is mostly customer-facing; leftover English UI and “Home” are peer-template residue. |

---

## Module 1: 3-second clarity (above the fold)

### What a first-time visitor actually sees (live)

1. **Value (H1):** “Finde dein Brautkleid in Gaggenau” — concrete service + city. **Pass.**
2. **Context:** “Boutique & Atelier” + “Private Brautberatung in ruhiger Atmosphäre, nur für dich.” **Pass.**
3. **Proof:** “5,0 ★ bei Google” and “persönliche Beratung & Änderungen im Atelier.” **Pass.**
4. **Primary CTA:** “Privaten Brauttermin anfragen” → `/termin`. **Pass** (high-contrast body button). Top-right nav is a text link labeled **Kontakt**, not a dominant action.

### Step 1.1 — Squint / blur

- Headline, proof stars, and the main button survive a squint.
- **Fail detail:** `<em class="italic-text"> Bevor du weiterliest: Stell dir vor, du stehst in deinem Kleid vor dem Spiegel – und weißt einfach: Das ist es.</em>`  
  That is textbook aesthetic narcissism: it asks the bride to attend a scene instead of stating an outcome.

**Designer (unpublished) replacement already written:**

- Italic: “Der Salon ist für deinen Termin reserviert – ohne fremde Blicke.”
- Subline: “Verliebe dich in ein Brautkleid oder erschaffe mit Ellen dein Unikat.” (was Sie-form)

### Step 1.2 — Scan path

| Expected | Live |
| :--- | :--- |
| Top-left brand | Elana logo. **Pass.** |
| Top-right direct action | “Kontakt” text link to `/termin`. **Weak.** Should read like the page CTA: **Termin anfragen**. |
| Mid-left H1 + subtitle + CTA | Present. **Pass**, once the italic is replaced. |
| Mobile stacked hierarchy | Stacked. Search overlay is a tap, not a horizontal trap. Mobile menu still says **Home** (English) and **Kontakt** → `#kontakt` (footer), not `/termin`. |

### Step 1.3 — Subhead precision

Concrete when it talks about a reserved salon, Ellen, and alterations. Generic when it cinema-directs (“Bevor du weiterliest…”). Footer still mixes **Sie** (“Ihre exklusive Adresse”) with **du** on the rest of the homepage.

---

## Module 2: Scroll ergonomics & interaction friction

### Step 2.1 — Native scroll physics

- No Lenis, GSAP ScrollSmoother, Spline, or canvas.
- Vertical scroll is OS-native.
- **Soft fails (novelty tax, not full scrolljacking):**
  - Hero is a Webflow **slider**.
  - Desktop trust/logo row uses **Splide autoscroll**.
  - Dress gallery: “Ziehe oder wische, um weitere Modelle zu entdecken.” Horizontal track is labeled, so it is not a hidden hover wall — still a second interaction grammar.

### Step 2.2 — Hover-to-reveal

- Review quotes, names, and process steps are visible by default. **Pass.**
- Dress cards are swipe/scroll, not hover-only. **Pass.**
- Search overlay is click-to-open; placeholder is English (`Search…` / `Search`). Friction is language, not concealment.

### Step 2.3 — Motion purpose

- 42 `data-w-id` interaction hooks and 54 inline `opacity:0` starters on the homepage.
- Custom CSS already forces the hero title visible (`opacity:1!important`) because interactions were hiding LCP text. That is a patch over a motion problem, not craft-through-clarity.
- **Fail if** headings still fade in after the user has scrolled past them. Treat remaining Webflow interactions as delete-key candidates: keep only if they finish in < 150ms.

---

## Module 3: Speed, latency & token-burning performance

**Targets from the brief:** LCP ≤ 1.8s, INP ≤ 150ms, CLS ≤ 0.05, JS < 300KB compressed. Live lab metrics were not captured (PSI 429).

### What is already doing the right job

- No autoplaying hero video, no WebGL.
- Local **Inter Tight** woff2 (weights 400/500/600/700) + **Great Vibes** for display; `font-display: optional`; Arial fallback metric override.
- LCP image preload (AVIF, `fetchpriority="high"`).
- Homepage CSS kills mobile video / extra thumbnails; defers extra slider backgrounds until `elana-slides-ready`.
- AVIF swap map in site head for a handful of CMS images.

### Remaining taxes

| Asset / behavior | Why it fails the video’s “delete key” |
| :--- | :--- |
| jQuery 3.5.1 + Webflow JS | Default Webflow payload; not a shader pack, still real JS. |
| Splide autoscroll | Continuous main-thread / compositor work for decoration. |
| Hero slider extra slides | Delayed BGs (good), but still a carousel instead of one still. |
| Cookie banner (first visit) | Large footer custom code; covers the primary CTA on mobile until dismissed. |
| Great Vibes | Second family for flourish. Keep only if it carries brand recognition; otherwise Inter Tight alone is clearer. |
| 4 Inter Tight weights | Brief asks max 2–3 weights. 400 + 500 + 700 would be enough. |

### Step 3.3 — CLS

Hero and many images are dimensioned via background CSS rather than `<img width/height>`. The performance pack’s `scrollbar-gutter: stable` and delayed slider BGs are CLS-aware. Cookie banner insert is a layout competitor on first visit.

---

## Module 4: Outcome-driven “delete-key” matrix

### Keep (clarifies offer, trust, or next action)

- H1 + city
- 5,0 ★ Google + named reviews (Daniela, Jessica, Kim)
- “Schneiderin mit Diplom” / Atelier alterations
- Process: Vorab → Privat ankommen → Mit Ellen auswählen
- Three checks: Silhouette / Bewegung / Machbarkeit
- Primary CTA → `/termin`
- `/termin` form: name, email, phone, two dates, wedding date, size, budget bands, wishes, consent + tel/WhatsApp fallbacks

### Simplify

- Hero italic → outcome line (already in Designer, unpublished)
- Nav “Kontakt” → “Termin anfragen”; mobile “Home” → “Startseite”
- One visible reviews H2 (Designer still holds several copies of “Keine fremden Blicke…”)
- Splide marquee → static proof strip or CSS-only
- Hero slider → single still + optional fade (or keep one image)

### Delete or quarantine

| Item | Why |
| :--- | :--- |
| Cinematic “Stell dir vor…” italic | Does not inform or convert |
| English Search / Newsletter chrome | Breaks scan trust on a German bridal site |
| Leftover ecommerce routes `/checkout`, `/paypal-checkout`, `/order-confirmation`, `/product`, `/sku` | Template residue; confuses crawlers and some visitors |
| Draft location pages (Offenburg, Pforzheim, Sinzheim) | Fine as drafts; do not publish until copy is conversion-complete |
| 404 title “Not Found” / 401 “Protected page” | English system pages |

### Typography / CTA hierarchy

- Body type is Inter Tight; contrast on the dark hero overlay needs a sunlight check (not measured in lab).
- **One dominant CTA per section** is mostly true. Nav should stop competing as a quiet “Kontakt” and become the same action in outline/solid button form.
- Secondary “Mehr über Ellen” is correctly subordinate on the closing band.

---

## Module 5: Trust, social proof & decision friction

### Step 5.1 — Proof visibility

- 5,0 ★ and review quotes sit near the first decision fold. **Pass.**
- Credentials (Schneiderin mit Diplom, Atelier) sit in the passform section, not only in the footer. **Pass.**
- Google count “99” is in the footer, not next to the hero stars. Move the **count** next to 5,0 ★.

### Step 5.2 — Action path

| Path | Taps from homepage | Verdict |
| :--- | ---: | :--- |
| Hero CTA → `/termin` → submit | 2 (land + submit) | **Good.** Form asks for real booking facts, not a novel. |
| Desktop nav “Kontakt” | 2, but label is vague | Relabel. |
| Mobile menu “Kontakt” | Scrolls to `#kontakt` footer | **Fail.** Should be `/termin` or tel/WhatsApp. |
| WhatsApp / phone in footer | 1 tap (`tel:`, WhatsApp) | **Pass.** |
| Cookie banner | Extra tap before CTA on first visit | Acceptable legally; keep collapsed on mobile (already done). |

`/termin` is the conversion engine the video describes: two Wunschtermine, wedding date, size, budget from **1.200–1.800 €** upward, wishes, consent, German success/error, phone + WhatsApp fallback. Expectation copy is explicit: *Anfrage ≠ Bestätigung; no model availability promise.*

### Step 5.3 — Expectation transparency

Answered on-site:

- How the appointment works (reserved salon, Ellen personally)
- Process steps
- Alterations honesty (“hängt von Schnitt, Konstruktion, Material und Zeitplan ab”)

Not on the homepage:

- Price orientation (“Viele Kleider beginnen bei etwa 1.200 €” lives on `/termin` and `/faq/budget-kauf`)
- Typical appointment length (mentioned on some location pages, not in the hero)

---

## Prioritized fixes

### P0 — Ship with next publish (already in Designer, unpublished)

1. Replace live hero italic with the reserved-salon line (Designer already holds the new string).
2. Keep Du-form subline (“Verliebe dich…”) — Designer already holds it.
3. Desktop Navbar Link **Kontakt → Termin anfragen** (still points to `/termin`).
4. Mobile menu label **Kontakt → Termin anfragen** and href **`#kontakt` → `/termin`**.
5. Mobile/desktop **Home → Startseite**.
6. Search button **Search → Suchen**. Newsletter button **Zum Newsletter anmelden**, loading **Bitte warten...**, success/error in German.
7. Placeholders `Search…` and `Enter your email` are **not writable** via the Data API (`placeholder` is a reserved attribute / missing setting key). Change them in the Designer form panel before publish.

### P1 — High ROI, small surface

6. After publish, confirm no remaining nav item still scrolls to `#kontakt`.
7. Put “ab ca. 1.200 €” as a single quiet line under the hero CTA or next to Google stars.
8. Put “99 Google-Bewertungen” next to the hero 5,0 ★.
9. Confirm newsletter placeholders are German in Designer (buttons and messages are already updated unpublished).
10. Homepage Open Graph image is empty — add one dress/salon still for shares.

### P2 — Delete-key / performance

11. Collapse duplicate review H2s in Designer (several copies; one live heading is enough). Do not mass-delete without checking visibility.
12. Stop Splide autoscroll; static logos/proof.
13. Reduce Webflow entrance animations; keep hero instantly visible (pack already forces this).
14. Drop unused ecommerce template pages from the sitemap or noindex them.
15. Align footer to Du **or** Sie; don’t mix.

---

## `/termin` vs. homepage (what “good” already looks like)

The booking page already follows the video:

- H1: “Dein Brauttermin. Ganz für dich.”
- Immediate facts: reserved salon, Ellen, alterations in-house
- Dual CTA: form + `tel:+497222406652`
- Proof chips: kostenlos, keine Laufkundschaft, Änderungen im Atelier
- Transparent budget bands and “Anfrage ist noch keine Bestätigung”

The homepage’s job is to get a scanning bride onto that page in one glance. Anything that delays that glance (cinema italic, “Kontakt”, English Search, cookie wall, marquee) is the remaining commercial debt.

---

## Designer IDs touched (unpublished)

| Change | Component / element |
| :--- | :--- |
| Hero italic (prior session) | `05703a61-ea48-f8b2-9b9b-7d5ac375901a` |
| Hero Sie → Du (prior session) | `05703a61-ea48-f8b2-9b9b-7d5ac375902d` |
| Desktop nav “Termin anfragen” | Navbar Link instance `72846a95-17c4-458c-0fd9-7e8ce74c00a5`, prop `651f8311-48ac-b936-3a09-5206807b5139` |
| Mobile nav label | Navbar `4f8993ca-…babc` / string `…baea` |
| Mobile nav href → `/termin` | Link `…bae8` |
| Navbar “Home” → “Startseite” | `301b6d42-…ebe5f`, `…bad7` |
| Search button “Suchen” | Search Wrap `17813dd9-…804d` / `…8050` `buttonText` |
| Newsletter button + loading DE | Form `9afd2c0d-…7219` / `…7223` |
| Newsletter success / error DE | Strings `…7226`, `…722b` |

**Do not publish from this audit unless Ellen/ops explicitly ask.** Use the usual Webflow publish checklist (staging preview, form test, cookie banner on a clean mobile session).

---

## What this repo is for

The GitHub repo does not contain the live Webflow project. This document is the durable audit artifact. Live conversion fixes live in the Webflow Designer until published to `elana-brautmode.de`.
