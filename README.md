# Silla Green · website V2

> V1 was the holding page at `sillaglobal.com/silla-green.html`, built to complete the Huawei partner registration.
> This is the market-ready replacement. It ships as its own repo and its own Vercel project.

Static site. No build step. Drop the contents of this folder into the repo root, push, import to Vercel with framework preset **Other**, leave build command and output directory empty.

Built on Ronney Stengert's 2026 proposal deck so print and web carry one CI. Colours were sampled directly from the PDF rather than guessed.

---

## Brand tokens

| Token | Value | Where it came from |
|---|---|---|
| Sand | `#D9D6C5` | Deck background |
| Sand light | `#E7E4D8` | Derived tint for cards |
| Mint | `#94DAC9` | Deck accent panels |
| Mint deep | `#629084` | Deck duotone shadow |
| Charcoal | `#505151` | Deck headings and body |
| Ink | `#2E2F2F` | Derived, for web contrast |
| Obsidian | `#121917` | New. The dark corridor section only. |

**Typeface: Raleway only.** Weights 200, 300, 400, 500, 700, 800, latin subset, self-hosted in `assets/fonts`. No Google Fonts request, so the page renders identically on networks that block third-party CDNs.

One flag: the heavy display caps in the deck may be Montserrat rather than Raleway. The site is built entirely in Raleway per brand direction. If Ronney confirms the display face, it is a one-line swap in the `@font-face` block.

---

## What is Ronney's and what is new

**Straight from the deck:** the cover lockup and duotone treatment, "Powering Africa's electric future", the greener-future copy, the four stat tiles, EV Mobility three-card layout, the bus and SUV spec boards, the charging network trio, the four market-position pillars, the partner set, the four-phase roadmap, the leadership list, and the contact block.

**New, built from the agreed direction:**

- **The atoms / electrons / bits layer strip.** The thesis section reframes the business as three stacked layers rather than a product list. Atoms are the physical build, electrons are generation and charging, bits are the AI and telemetry. It is the clearest articulation of why this is an infrastructure company and not a car dealer.
- **"We turn electrons into economic throughput"** promoted to the thesis headline. Strongest line in the group's copy.
- **The dark corridor section.** A live-telemetry canvas where nodes are depots and the pulses are load moving between them. This is the real-versus-rendered balance we discussed: real footage frames sitting directly beneath a rendered network layer. Most infrastructure sites are all render and read as vapourware; most operator sites are all footage and read as small. The blend is the position.
- **Corridor status nodes** showing South Africa and Botswana as live, Uganda and the West and East Africa markets as dated. Honest, and it makes the roadmap feel operational rather than aspirational.

---

## Footage slots

The site is built to receive video. Four slots are marked in the HTML with `FOOTAGE SLOT` comments.

**Slot 01 · hero.** Replace the `<img>` inside `.hero .bed` with:

```html
<video autoplay muted loop playsinline poster="assets/img/hero-logistics.jpg">
  <source src="assets/video/hero.mp4" type="video/mp4">
</video>
```

The duotone and tint layers sit above it, so any footage automatically lands in CI. Aim for 8 to 12 seconds, no audio, under 4MB, 1920 wide.

**Slots 02 to 04 · the corridor strip.** Same swap inside each `.frame`. Short loops of the conversion floor, a depot charging session and the solar field.

Shot list worth getting on the Botswana or China trip, in priority order: a bus pulling into a charging bay and the connector going in; the conversion floor with people working; a drone rise over the solar field; a driver's-eye corridor run; the grid operations screens. Real people and real steel. That is the whole differentiator against every rendered competitor site.

---

## Before it goes live

1. **Domain.** Find and replace `REPLACE-WITH-DOMAIN.com` in `index.html`. The deck says `www.sillagreen.com`, which is not registered yet. Docky was asked to register it.
2. **Leadership photographs.** The team section is deliberately built **without portraits**. The portraits in the proposal deck are synthetic stand-ins, which is fine in a PDF sent to a counterparty and a real credibility risk on a public site that gets indexed and read by journalists. Add real headshots after the shoot, or leave the section as text.
3. **Confirm the sixth partner.** The crest logo in the deck is described only as "strategic investor and offtaker" and is currently unnamed on the site.
4. **Numbers check.** `$1B+` is a valuation *target*, and the site labels it that way. Keep that word. Dropping it turns an ambition into a claim.

---

## Files

| Path | What |
|---|---|
| `index.html` | Whole site. CSS and JS inlined. |
| `assets/logo-white.png` | Official white logo, unchanged. |
| `assets/fonts/` | Raleway, 6 weights, woff2, latin. |
| `assets/img/` | Imagery lifted from the proposal deck so web matches print. |
| `assets/favicon.svg` | Leaf mark on obsidian. |
| `og.png` | 1200x630 share card. |
| `robots.txt`, `sitemap.xml` | Indexing. |
| `vercel.json` | Caching and security headers. |

Roughly 1.5MB on first load, mostly imagery, all below-fold images lazy-loaded. If you want it lighter, the hero image is the single biggest file and a 10-second video would replace it anyway.

The corridor animation respects `prefers-reduced-motion` and stops entirely when it is set.
