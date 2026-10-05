# Stage A launch site

A complete, working Phase 2 site: one landing page that sells, a confirmation page,
and three legal pages. Static HTML and CSS, no build step, no dependencies.

**Everything here is placeholder content for a fictional example niche**
(PA school admissions, brand "Scrub In"). It exists so you can judge the structure
and the conversion mechanics with real copy rather than lorem ipsum. Replace all of
it before publishing.

## Files

| File | What it is |
|---|---|
| `index.html` | The landing page. Nine sections, in the order they should stay. |
| `thanks.html` | Post-purchase confirmation. Stripe redirects here after payment. |
| `privacy.html` | Privacy policy template |
| `terms.html` | Terms of service template |
| `refunds.html` | Refund policy template |
| `styles.css` | All styling. Design tokens are at the top. |

## Running it

Open `index.html` in a browser. That is the whole workflow — there is no build.

To deploy: push to any static host (Cloudflare Pages, Netlify, GitHub Pages).
Point the domain at it and you are live.

## What to change, in order

1. **Brand.** `Scrub In` appears in every file's masthead, footer, and `<title>`.
   The logo is a CSS circle mark (`.logo .mark`), not an image file, so there is
   nothing to export.
2. **Colors and type.** Both themes are defined as tokens in the `:root` block at
   the top of `styles.css`. Change the tokens; never hardcode a color in a
   component rule, or one theme will break.
3. **Every word of copy** in `index.html`. The section comments are numbered to
   match the outline.
4. **The readiness widget.** The `PROGRAMS` array at the bottom of `index.html`
   holds six fictional rows. Swap in your own data and rewrite `assess()` for
   whatever your niche's qualifying logic is. If your niche has no such
   calculation, delete the whole `.chart` block — do not keep it as decoration.
5. **Case studies.** Currently invented. Replace with real, permissioned outcomes
   or delete the section. Never publish a case study you cannot substantiate.
6. **Pricing.** Replace both `href="thanks.html"` buttons with your Stripe Payment
   Link URLs, and set the Stripe success URL to your deployed `thanks.html`.
7. **Legal pages.** These are templates describing practices you must actually
   follow. Have a lawyer review them.
8. **Delete the `.scaffold` banner** from all five pages. It is the one-line
   `<div class="scaffold">` under each `<body>`.

## Things that are deliberate

- **No card fields anywhere.** Payment buttons link out to Stripe-hosted checkout,
  which keeps you in PCI SAQ A. Do not add a card form to this site.
- **The renewal disclosure is styled as a warning, not a feature.** That is the
  `.renewal` block. Incumbents bury this in a benefits list; state auto-renewal
  laws are written about exactly that. Keep it visually distinct and adjacent to
  the price.
- **The free widget sits above the paywall.** Value visible before the ask. This
  is the whole thesis of the business model, expressed as page order.
- **Both themes are real.** Light and dark are defined at token level in three
  blocks (`:root`, the `prefers-color-scheme` media query, and `[data-theme]`)
  so the page follows the reader's system setting and any explicit override.
- **No tracking scripts.** Add cookieless analytics (Cloudflare Web Analytics or
  Plausible) rather than Google Analytics, and you avoid consent-banner
  obligations entirely.

## What this site deliberately does not have

Accounts, a database, a blog, or a community. Those are Stages B through D.
Shipping them now would be building before selling.
