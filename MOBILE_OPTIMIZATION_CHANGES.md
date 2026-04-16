# Mobile Optimization Pass — Full Site

**Date:** April 16, 2026
**Scope:** CSS-only mobile experience improvements applied to all 21 HTML pages.
**Risk level:** Low. No HTML, JS, copy, or desktop changes.

---

## What changed

### 1. Story Sprint FAQ max-height bug fix

`story-sprint/index.html`: `.faq-a.open` max-height increased from 300px to 1500px. Several new FAQ answers (Sprint+ explanation, multi-leader question, retainer credit policy) exceed 300px and were being silently truncated on expand.

### 2. Universal mobile optimization block

A consolidated CSS block was injected right before `</style>` on every page. Additive only: does not replace existing styles. Marked with a visible comment so it can be easily found and rolled back.

**At max-width 768px (phones and small tablets):**
- Section padding tightened: `clamp(4rem, 8vw, 7rem)` becomes `clamp(2.5rem, 6vw, 4rem)` - cuts roughly 1.5 screens of empty vertical space per page
- Body font reduced from 18px to 16px - 2026 mobile standard
- Card padding reduced from ~2.5rem to 1.5rem across all card types
- Gap between stacked cards reduced to 1rem
- FAQ tap targets enlarged to 1rem vertical padding
- Primary CTAs go full-width with stacked layout
- Line-heights tightened on h1/h2/h3

**At max-width 480px (small phones - iPhone SE, older Androids):**
- Container widened to 92vw
- Section padding tightened further
- Hero h1 capped at 2.6rem
- Card padding tightened to 1.25rem
- Nav logo shrinks to prevent wrapping
- Closing CTA headings wrap better

### 3. Selector coverage

The mobile block targets ~80 card and grid class names across the site. Including but not limited to: prod-card, freq-card, layer-card, tier-card, hiw-card, outcome-card, del-card, invest-card, example-card, foundation-body/header, approach-card, ba-card, big-number-card, case-card, cycle-step, detail-card, diff-card, dim-card, q-card, res-card, step-card, success-card, testimonial-card, wt-card, alt-tool-card, fact-card, format-card, evo-card, gate-card, insight-card, lane-card, pn-card, pq-card, result-card, form-card, founder-grid, posts-grid, client-grid, footer-grid.

---

## Pages updated (21)

All HTML files in the site:
- `/404.html`
- `/index.html` (homepage)
- `/about/index.html`
- `/blog/index.html`
- `/contact/index.html`
- `/content-cost-calculator/index.html`
- `/content-engine/index.html`
- `/content-pillars/index.html`
- `/executive-visibility/index.html`
- `/podcast-checklist/index.html`
- `/podcast-production/index.html`
- `/post-ideas/index.html`
- `/privacy-policy/index.html`
- `/resources/index.html`
- `/scorecard/index.html`
- `/services/index.html`
- `/story-sprint/index.html`
- `/strategic-partnerships/index.html`
- `/work/index.html`
- `/work/energy-capital/index.html`
- `/work/project-vanguard/index.html`

---

## What did NOT change

- No HTML structure changes
- No copy changes
- No JavaScript changes
- No color, brand, or identity changes
- Desktop experience unchanged (all new CSS is inside @media queries)
- Existing page-specific breakpoints (860px, 960px) preserved
- `_headers`, `sitemap.xml`, `robots.txt`, tracking tags, forms, PDFs all unchanged

---

## Bug check results

**Passed:**
- HTML validity: all 21 pages parse cleanly with lxml
- CSS syntax: balanced braces on every style block
- Cascade ordering: mobile block is always last in cascade, so overrides work as expected
- Injection count: exactly one mobile block per page
- Viewport tags: present on all 21 pages
- Story-sprint FAQ fix applied correctly

**Not verified by automated tests (verify manually after deploy):**
- FAQ accordion toggle behavior on story-sprint
- Calculator wizard flow on content-cost-calculator
- Scorecard multi-step flow
- Mobile hamburger nav menu
- Contact form Formspree submission
- These are all untouched by CSS-only changes but should be confirmed on an actual device

---

## Deployment

Same flow as the last update:
1. Upload zip to Cloudflare Workers and Pages via "New deployment"
2. Ensure `_headers` is included at root
3. Changes propagate within seconds

---

## Testing checklist after deployment

Test on an actual phone, not Chrome DevTools responsive mode.

- [ ] Homepage: scroll through, confirm sections feel tighter
- [ ] Story Sprint: expand each FAQ, confirm long answers fully display
- [ ] Story Sprint: confirm Sprint vs Sprint+ cards stack cleanly
- [ ] Services: FAQ native details elements still expand
- [ ] Podcast Production: production option cards stack with reduced padding
- [ ] Strategic Partnerships: tier cards stack cleanly, featured tier stays prominent
- [ ] Contact: form submits correctly on mobile
- [ ] Content Cost Calculator: wizard flow completes
- [ ] Scorecard: multi-step flow works
- [ ] Blog / Post Ideas: idea cards render correctly
- [ ] Work pages: case studies, metrics display correctly
- [ ] 404: displays properly
- [ ] On iPhone SE: hero headlines don't overflow

---

## Rollback

Each page can be rolled back by finding the comment `MOBILE OPTIMIZATION BLOCK (added 2026-04-16)` in the style block and deleting from that comment down to just before `</style>`. On story-sprint, also revert `max-height: 1500px` to `max-height: 300px` if needed.

---

## Follow-up recommendations (not applied)

These are bigger changes that deserve their own review and testing cycle:

1. Convert card grids to swipe carousels on mobile for podcast-production (prod-cards, freq-cards, layers-grid) and strategic-partnerships (tiers-grid). Requires HTML + JS changes.
2. Progressive disclosure on feature cards: show card title + summary + "See what's included" expand. Requires HTML changes.
3. Sticky mobile CTA bar on every page. Podcast-production has the foundation (body padding-bottom + mobile-cta class); extend site-wide.
4. Consolidate the mobile block into a shared CSS file instead of duplicating it across 21 inline style blocks.

---

*ClarityForge Studios — Mobile Optimization Pass — Full Site*
