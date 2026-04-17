# Mobile Optimization Pass v2 — Full Site

**Date:** April 16, 2026
**Scope:** Real-world bug fixes based on phone screenshots, plus site-wide mobile CSS improvements.

---

## Bugs fixed in this pass

### 1. Hero CTA secondary link stretched full-width (caused by v1 mobile block)

The v1 mobile block used `align-items: stretch !important` on `.hero-ctas`, which stretched every child including secondary text links. On the homepage this caused the "Explore our free tools and resources" underlined link to span the full viewport width, which looked wrong.

**Fix:** Changed selector to only target direct `.btn-primary` children. Secondary links stay inline at their natural width. Also changed `align-items` back to `flex-start` and tightened `gap` to `1rem`.

### 2. Horizontal overflow on homepage (pre-existing site bug)

The `.gap-states` flex container (holding the "Without a system" / "With ClarityForge" before/after cards) had no mobile breakpoint. It stayed as `display: flex` horizontal at all widths, causing the second card to extend off-screen. This pushed the entire page wider than the viewport, which compressed every section above into a narrow column — making the hero, problem section, and headings all look broken.

**Fix:** Added `.gap-states { flex-direction: column; gap: 1rem; }` inside the existing 960px media query on the homepage.

### 3. Hamburger menu broken on 18 of 21 pages (pre-existing site bug)

The `<button class="nav-hamburger">` element had styling but no click handler on 18 pages. Only `content-cost-calculator` and `privacy-policy` had the working implementation. Tapping the menu button did nothing.

**Fix:** Added the working `onclick` attribute from content-cost-calculator to all 18 broken pages. The CSS for the open state (`.nav-links.nav-open`) already existed on every page, so no CSS changes needed.

---

## All changes in this deploy

### From v1 (mobile optimization pass)
- Story-sprint FAQ max-height bug fix (300px → 1500px)
- Universal mobile optimization block on all 21 pages
  - Tighter section padding at 768px and 480px
  - 16px body font on mobile (2026 standard)
  - Reduced card padding (~1.5rem from ~2.5rem at 768px)
  - Reduced gap between stacked cards (1rem from 2rem)
  - FAQ tap targets enlarged
  - Line-heights tightened on headings

### New in v2
- Hero CTA selector fixed (only targets `.btn-primary`, not secondary links)
- Homepage `.gap-states` stacks on mobile
- Hamburger onclick handler added to 18 pages

---

## Pages with changes

All 21 HTML files touched. Full list: `404.html`, `index.html`, `about/index.html`, `blog/index.html`, `contact/index.html`, `content-cost-calculator/index.html`, `content-engine/index.html`, `content-pillars/index.html`, `executive-visibility/index.html`, `podcast-checklist/index.html`, `podcast-production/index.html`, `post-ideas/index.html`, `privacy-policy/index.html`, `resources/index.html`, `scorecard/index.html`, `services/index.html`, `story-sprint/index.html`, `strategic-partnerships/index.html`, `work/index.html`, `work/energy-capital/index.html`, `work/project-vanguard/index.html`.

---

## Known remaining issues not fixed in this pass

1. **35 other flex containers across the site have no mobile stacking rule.** Automated scan flagged them, but they're mostly small inline elements (icon-text rows, button rows, labels) that are naturally narrow. Not likely to cause overflow. If specific pages show similar bugs after deploy, we fix surgically.
2. **404 page h1 stays at 5rem on mobile** — might feel too big on small screens. Original designer choice, not introduced by this pass.
3. **Mobile block still contains redundant `body { font-size: 16px }`** — every page already had this rule in their existing 768px media query. Duplicate is harmless but wasted bytes.

---

## Testing checklist after deployment

Test on an actual phone:

- [ ] Homepage: tap hamburger menu in top right — menu should open
- [ ] Homepage: scroll past hero, confirm page doesn't scroll horizontally
- [ ] Homepage: "Without a system" and "With ClarityForge" cards should stack vertically, not side-by-side
- [ ] Homepage hero: "Explore our free tools and resources" link should be inline text, not full-width underline
- [ ] Every other page: tap hamburger, menu opens
- [ ] Story Sprint: expand each FAQ, confirm long answers display fully
- [ ] Services, Contact, Content Cost Calculator, Scorecard: spot-check flows
- [ ] On iPhone SE (smallest supported): hero headlines don't overflow

---

## Rollback

Each page can be rolled back individually:
1. Mobile CSS block: find the comment `MOBILE OPTIMIZATION BLOCK (added 2026-04-16)` and delete from there to just before `</style>`
2. Hamburger onclick: delete the `onclick="..."` attribute from `<button class="nav-hamburger">`
3. Homepage `.gap-states`: remove the single line from the 960px media query

---

*ClarityForge Studios — Mobile Optimization v2*
