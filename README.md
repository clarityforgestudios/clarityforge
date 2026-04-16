# ClarityForge Site Update — Voice Profile Pricing + Foundation Build

**Date:** April 16, 2026
**Files changed:** 7 pages

---

## What's in this zip

Seven updated pages, each in its proper folder structure for direct upload to Cloudflare Workers & Pages:

- `story-sprint/index.html` — Sprint vs Sprint+ pricing, new FAQ items, multi-voice callout
- `strategic-partnerships/index.html` — **NEW Foundation Build section**, tiers renumbered as Step 2
- `contact/index.html` — Updated dropdown context messages
- `services/index.html` — FAQ updated with Sprint+ mention
- `resources/index.html` — Voice Profile Questionnaire card tightened, Sprint pricing updated
- `podcast-production/index.html` — Sprint callout updated
- `content-cost-calculator/index.html` — Results page CTA updated

Plus `CHANGES_SUMMARY.md` with full change log.

---

## Deployment

1. Download this zip
2. Go to Cloudflare Workers & Pages dashboard
3. Open the clarityforgestudios project
4. Click "Create deployment" → "Upload assets"
5. Upload the contents (each folder with its index.html)
6. Changes go live within seconds

**Note:** This is a partial update. Your existing deployment has 20 pages. These 7 replace the corresponding pages in the existing deployment. Do NOT delete the other 13 pages.

---

## Quick visual check after deploy

- [ ] Visit `/story-sprint` — confirm Sprint vs Sprint+ cards render side-by-side on desktop, stack on mobile, RECOMMENDED badge is gold
- [ ] Visit `/strategic-partnerships` — scroll to Foundation Build section (between "How It Works" and pricing tiers). Confirm navy header band, two-column body, gold accents
- [ ] Click through Story Sprint FAQ items — all 7 should expand
- [ ] On `/contact`, change dropdown — each option should show the updated context message
- [ ] On mobile, confirm Foundation Build two-column body stacks correctly
