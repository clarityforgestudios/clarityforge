# Voice Profile Pricing Update — Site Changes Summary

**Date:** April 16, 2026
**Updated files:** 6 pages
**Project file reference:** /mnt/project/ClarityForge_Website_Project.md

---

## Pricing decisions applied

Based on the Voice Profile Pricing Dial-In analysis:

- **Story Sprint** — Framed as "$500 for individuals, $750 for organizations" (range clarified, not collapsed)
- **Story Sprint+** — New upgrade: $750 / $950 (Sprint + Voice Profile, $200 bundle discount off $450 standalone Voice Profile value)
- **Voice Profile standalone** — $450 value (not offered as its own purchase path, only as Sprint+ upgrade or retainer onboarding)
- **Credit policy** — 100% of Sprint or Sprint+ fee applies to Month 1 of retainer, capped at the retainer's first-month fee. If retainer is less than Sprint+, the first month is complimentary.

---

## Pages updated (6)

### 1. `/story-sprint/index.html` — Primary changes
- Hero micro text: "$500 for individuals. $750 for organizations. Every ClarityForge engagement starts here."
- **Investment section completely rebuilt** as a two-card side-by-side comparison:
  - Story Sprint card ($500 / $750)
  - Story Sprint+ card (featured, $750 / $950, marked RECOMMENDED)
  - Each card lists its deliverables and scope
- New CSS for `.invest-card` and `.invest-card-featured` (side-by-side responsive grid, stacks on mobile)
- Credit policy block clarified: explains cap and complimentary-first-month scenario
- FAQ expanded from 4 to 7 items, adding:
  - "Why is the price a range?"
  - "What is the Story Sprint+ upgrade?"
  - "How does the first-month retainer credit work?"
- Closing CTA micro text updated
- Meta description, OG description, Twitter description all updated for search/social

### 2. `/contact/index.html`
- Four dropdown context messages updated to reflect new pricing structure and mention Sprint+ where relevant
- Podcast context: "$500 individuals / $750 organizations. Upgrade to Sprint+ for a Voice Profile."
- Executive Visibility context: mentions Sprint+ for LinkedIn and executive content
- Story Sprint context: full pricing explanation with 100% credit note

### 3. `/services/index.html`
- FAQ item "What does the first month look like?" updated to mention both Sprint and Sprint+ options with explicit pricing

### 4. `/resources/index.html`
- Voice Profile Questionnaire card description tightened: "Fill it out, send it back, and we'll review on a 20-minute call and tell you whether a Story Sprint is the right next step."
- Featured Story Sprint block in footer: price line updated to "$500 individuals. $750 organizations. Upgrade to Sprint+ for a Voice Profile."

### 5. `/podcast-production/index.html`
- Story Sprint callout block updated to mention both Sprint and Sprint+ with explicit pricing for each

### 6. `/content-cost-calculator/index.html`
- Results page CTA sub-text updated to reflect new pricing structure

---

## Pages NOT updated (intentional)

These pages have "Start a Story Sprint" buttons that link to `/story-sprint`. Since the Sprint page itself now explains the full pricing structure, these button-only references don't need changes:

- `/index.html` (homepage)
- `/about/index.html`
- `/executive-visibility/index.html`
- `/strategic-partnerships/index.html`
- `/blog/index.html`
- `/work/index.html`, `/work/energy-capital/`, `/work/project-vanguard/`
- `/scorecard/index.html`
- `/content-pillars/index.html`
- `/post-ideas/index.html`
- `/podcast-checklist/index.html`
- `/privacy-policy/index.html`
- `/404.html`

The Sprint page is now the single source of truth for pricing detail. Other pages route prospects there via CTAs. This prevents pricing drift between pages.

---

## Validation

All 6 updated pages pass HTML parsing. No broken tags, no orphaned elements.

Cross-checked for any remaining "$500-$750" or "$500-750" references. The only remaining instances are in `/podcast-production/index.html` Strategy Layer pricing (+$500-$750/mo for Narrative Strategy and Growth + Performance) — these are unrelated to Story Sprint and should stay as-is.

---

## Deployment notes

Per the project file deployment workflow:
1. Download the updated site zip from Claude
2. Upload to Cloudflare Workers & Pages dashboard via "New deployment"
3. Ensure `_headers` file is included at root
4. Changes propagate within seconds

No changes needed to:
- `_headers` file (CSP allowlist unchanged)
- `sitemap.xml` (no new pages)
- `robots.txt`
- Tracking tags (GA4, Clarity, LinkedIn Insight) — all unchanged
- Formspree endpoint
- Footer structure

---

## Testing checklist after deployment

- [ ] Story Sprint page: verify Sprint vs Sprint+ cards render correctly on desktop (side-by-side) and mobile (stacked)
- [ ] Story Sprint page: verify gold "RECOMMENDED" badge appears on Sprint+ card
- [ ] Story Sprint page: click through all 7 FAQ items to verify they expand
- [ ] Contact page: click through each dropdown option to verify new context messages display
- [ ] Services page: expand "What does the first month look like?" FAQ
- [ ] Resources page: verify Voice Profile Questionnaire download link still works
- [ ] Podcast production page: scroll to Sprint callout to verify new copy
- [ ] Content Cost Calculator: complete the wizard flow to verify updated CTA sub-text displays on results

---

*ClarityForge Studios — Voice Profile Pricing Update*
