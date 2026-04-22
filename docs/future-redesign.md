# Future redesign brief — v2 website

## Context

The current site (shipped April 2026) is deliberately restrained: serif headings,
two-colour palette (navy + copper), zero imagery, hand-written static HTML. That
aesthetic was chosen to read as "real business" to OpenAI org-verification
scrapers and to ship in a single afternoon.

Once verification comes through, there's room to warm the site up into something
that actually sells the services — less clinical, more like a considered
engineering studio.

## When to do it

Wait until **all three** are true:

1. OpenAI org verification has come through (don't change anything the verifier
   scrapers have indexed until they've crawled and approved)
2. There are 2–3 real projects we can feature as case studies (real is always
   better than fabricated — anonymise clients as needed but the work should be
   genuine)
3. There's appetite to spend a day or two on it — no urgency, the current site
   does its job

## What "less clinical" means

### Hero imagery
- Real photo of a harness / ECU / bench setup — phone camera is fine with good
  light, a desk lamp and a black cloth background go a long way
- Or a hero render: car cutaway showing wiring routing, exploded harness view,
  something that signals "we design this stuff"
- Shot with intent — moody lighting, shallow depth of field, not stock

### Case studies / projects section
- 2–3 anonymised projects, each with a photo/diagram and a short write-up
- Examples of the shape: "Formula Student team control system", "EV conversion
  wiring harness for [marque]", "Motorsport telemetry CAN gateway"
- This is what buyers actually scan for — it's the single highest-impact
  addition

### Process section
- "How we work" with icons or small illustrations for the 4–5 phases:
  concept → schematic → harness design → prototype → production release
- Establishes methodology without needing case studies to exist yet

### Team / founder section
- Photo + short bio of Fergus
- Establishes that there's a real person behind a real company — matters for
  trust signals on a services site

### Typography upgrade
- Pair a proper serif (Fraunces / Source Serif 4 / Tiempos) with a technical
  sans (Inter for body, JetBrains Mono for callouts)
- Still corporate, but more considered than system-font fallbacks

### Micro-interactions
- Subtle scroll-triggered fades
- Possibly a hero video loop (harness being built, oscilloscope traces, etc.)
- Hover states on project cards
- Restrained — not a framer-motion festival, just polish

### Blog / insights (optional)
- 3–4 articles on control-systems topics positions EVM as thought leaders and
  helps SEO
- One post per quarter is plenty — MDX files in the repo are fine until there
  are 10+ articles
- Example topics: "Choosing CAN vs LIN for body electronics", "Why we cap
  conductor gauge changes at each splice", "EV conversion wiring: lessons from
  a ground-up rebuild"

## Tech stack for v2

- **Astro** — same simplicity as static HTML, but gives us components, MDX for
  articles, and automatic image optimisation. Works with GitHub Pages via a
  build action.
- **Keep GitHub Pages** initially. Consider Cloudflare Pages later if we need
  forms (contact), edge functions, or analytics beyond plausible.io-style
  static tracking.
- **Images** — shoot real workshop/bench photos on a phone with decent light;
  supplement with 1–2 commissioned 3D renders if needed for hero shots.
- **CMS** — unnecessary at first. MDX files in the repo are fine until we have
  a real publishing cadence.
- **Fonts** — self-host through Fontsource or bunny.net to avoid Google Fonts
  privacy issues (and shaving a DNS lookup).

## Migration plan

1. Create `v2` branch; scaffold Astro project alongside existing static files
2. Port `index.html`, `privacy.html`, `terms.html` to Astro components
3. Verify rendered HTML still contains the same verification-critical content
   (company number, registered office, privacy/terms links)
4. Build + deploy to a preview URL (GitHub Pages preview action or a
   `v2.evmotive.co.uk` subdomain for staging)
5. Add new sections (case studies, process, team) incrementally — ship each
   one on `main` as soon as it's ready rather than doing a big-bang launch
6. Keep the same `CNAME` + DNS — no change to the public domain

## Known constraints / gotchas

- **Don't break crawler URLs** — OpenAI's verification crawler may have cached
  specific paths. Keep `/privacy.html` and `/terms.html` working (or
  server-side redirect them to new paths if restructuring)
- **Company info must stay on the about page** — the registered office +
  company number are what OpenAI verifiers look for
- **Keep the site statically hosted** — dynamic features (forms, auth) add
  attack surface and complexity for a services site that gets a handful of
  visitors per week

---

_Brief captured April 2026 during initial site launch. Revisit once OpenAI
verification completes._
