# PAIR — landing page

Marketing site for **PAIR**, a platform that helps ambitious people find, evaluate and
test a potential business partner before committing to building a company together.

> Build with the right person.

**Meet → Match → Test → Build.** The differentiator is the *Founder Trial*: a short week
of real work together, scored on partnership signals, before anyone splits equity.

## What's here

```
index.html    the entire site — markup, styles and script in one file
```

No build step, no dependencies, no framework. The only external request is the Google
Fonts stylesheet (Familjen Grotesk, Hanken Grotesk, IBM Plex Mono); every face declares a
system fallback, so the page degrades cleanly if it's blocked.

## Run it locally

```bash
python3 -m http.server 8000
# → http://localhost:8000
```

Or just open `index.html` in a browser.

## Deploy

Static hosting, root directory, no build command:

- **Cloudflare Pages** — connect this repo, framework preset *None*, output directory `/`
- **Vercel** — import the repo, framework preset *Other*
- **Netlify** — publish directory `/`

Then point your domain at it. Every push to `main` redeploys.

## Design system

| | Light | Dark |
|---|---|---|
| Background | `#F4F4F7` | `#09090F` |
| Text | `#0B0B14` | `#EDEDF3` |
| Hairlines | `#DCDCE5` | `#232330` |
| Accent (electric ultramarine) | `#2A17F5` | `#7565FF` |
| Signal amber — friction blocks only | `#8F5312` | `#D69553` |

Type: **Familjen Grotesk** for display, **Hanken Grotesk** for body, **IBM Plex Mono** for
data and labels. One accent colour; the amber is semantic and appears only in the
"Potential challenge" block of a profile card.

The structural idea is the **seam** — the page is built from unequal halves meeting at a
1px rule, so the pairing is in the layout rather than in illustration. The wordmark is
`PA|IR`, with the seam in the accent colour.

Everything is driven by CSS custom properties on `:root`, with the full token set
redefined for `prefers-color-scheme: dark` and for `[data-theme]`. The Founder Trial and
closing CTA are `.invert` panels: they redeclare the tokens locally, so they stay dark in
both themes.

## Honesty rules baked into the content

- No testimonials, no customer logos, no user counts, no invented statistics.
- Every profile and metric is labelled **Product preview** / **example profiles**.
- Profile cards show compatibility *and* the likely point of friction.

Keep it that way until there are real numbers to put up.

## Known gaps

- [ ] **The founding-cohort form doesn't persist anything.** It validates and shows the
      success state, but submissions go nowhere. Wire it to Formspree, Airtable, Supabase
      or your own endpoint before driving traffic to it.
- [ ] Privacy / Terms / Contact in the footer link to the cohort section — they need real pages.
- [ ] Add `<link rel="canonical">` and an absolute `og:image` once the domain is live
      (there's a TODO comment in the `<head>`).
- [ ] No analytics.

---

© 2026 PAIR. All rights reserved.
