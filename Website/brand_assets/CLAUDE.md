# CLAUDE.md — E.A Car Wash and Polishing Website

## Project Overview
Marketing website for **E.A Car Wash and Polishing**, a mobile car wash and detailing service based in Manama, Bahrain. They travel to the customer's location to wash, vacuum, and polish vehicles. Their primary differentiator is the visible "before & after" transformation work (especially deep interior cleaning).

The website's primary job is to **convert visitors into a WhatsApp conversation** — that's where bookings actually happen.

---

## Business Details

### Contact
- **WhatsApp (primary CTA):** +973 33018656
  - Click-to-chat URL: `https://wa.me/97333018656`
  - Pre-filled message URL: `https://wa.me/97333018656?text=Hello%2C%20I%27d%20like%20to%20book%20a%20car%20wash`
- **Instagram:** [@ea.car_wash](https://www.instagram.com/ea.car_wash/)
- **Threads:** `ea.car_wash`
- **Facebook:** `Ea car wash`
- **Service area:** Manama, Bahrain (mobile — confirm full coverage area with client)

### Services & Pricing (BHD)

| Tier | Small (صغير) | Medium (متوسط) | Large (كبير) | Includes |
|------|-------------|----------------|--------------|----------|
| **Shine Wash** | 6 | 7 | 8 | Exterior wash, exterior quick wash |
| **Premium Wash** | 18 | 19 | 21 | Exterior wash with foam, interior wash |
| **Luxury Wash** | 25 | 26 | 27 | Exterior wash with foam, 3-step exterior polishing, interior vacuum, [confirm full list with client] |

> ⚠️ **Pricing caveat:** Their current marketing materials show "before/after" prices as if perpetually discounted (e.g. 7 BD struck through → 6 BD). The values above are the *current* advertised prices. Before launching the site, confirm with the client whether these are permanent or a promotional period. Permanent fake "discounts" on a website look manipulative and hurt trust over time.

> ⚠️ **Copy fix:** Their materials say "**median**" for the middle vehicle size. The correct word is "**medium**." Do not propagate the typo to the new site.

### Vehicle Size Examples (confirm with client)
- **Small:** sedans, hatchbacks
- **Medium:** crossovers, mid-size SUVs
- **Large:** full-size SUVs, pickups, vans

### Specializations (from Instagram highlights)
- Deep interior cleaning
- Before/After transformation reels (their strongest social proof — feature heavily)
- Polishing
- Mobile-only convenience

---

## Branding

### Logo
- Red circular badge with white outer border and inner black ring
- Cartoon red sports car mascot, anthropomorphized (eyes, smile), holding a hose, spraying water with bubbles
- "EA" in white serif lettering on a red banner across the bottom
- Tone: friendly, energetic, family-friendly — **not luxury detailing**

### Color Palette (extracted from logo + marketing)
| Use | Approx. Hex |
|-----|-------------|
| Primary red | `#E31E24` |
| Secondary cyan/blue | `#1FB6E5` |
| Accent yellow (price highlights) | `#FFEB3B` |
| Black, white | as needed |

> Designer note: the cyan-and-yellow Instagram graphics are loud and a little dated. The new site should keep the red brand color but use cyan and yellow more sparingly — large fields of these colors won't read as professional.

---

## Languages
**Bilingual required: English + Arabic (RTL).**
- Existing materials mix both languages awkwardly.
- Implement a clean language toggle.
- Use `dir="rtl"` and logical CSS properties (`margin-inline-start`, etc.) — not `margin-left`-based layouts that break in RTL.
- Numerals: use Western Arabic numerals (1, 2, 3) for prices in both languages — common practice in the Gulf.

---

## Recommended Site Structure

1. **Hero** — value prop ("Mobile car wash & polishing — we come to you in Manama"), WhatsApp CTA, photo of clean car or team in action
2. **Services & Pricing** — three tier cards (Shine / Premium / Luxury); each card has a "Book on WhatsApp" button that pre-fills a tier-specific message
3. **Before & After Gallery** — their strongest asset. Use a draggable comparison slider component. Lead with the dirty-seat → clean-seat shots and the floor mat shots.
4. **How It Works** — 3 steps: (1) Message us on WhatsApp, (2) We come to your location, (3) Pay on completion
5. **Service Area** — map or list (confirm coverage with client)
6. **Trust signals** — Instagram embed showing recent posts, customer count, years in business (if they have it)
7. **Contact footer** — WhatsApp, Instagram, phone, hours

### Critical UX rules
- WhatsApp button must be sticky/floating on mobile — that's the entire conversion path
- Service cards should pre-fill the WhatsApp message with the chosen tier and size
- Mobile-first — Bahrain traffic is overwhelmingly mobile

---

## Recommended Tech Stack (pending client confirmation)
- **Framework:** Next.js (App Router) — SEO matters for "car wash Manama" Google searches
- **Styling:** Tailwind CSS
- **Image optimization:** `next/image` with WebP
- **i18n:** `next-intl` for EN/AR with full RTL support
- **Hosting:** Vercel (free tier fine for this scale) or Cloudflare Pages
- **Analytics:** Plausible or simple GA4
- **No CMS needed initially** — content is small and stable; hardcode in MDX or JSON. Add a CMS only if they want to update prices/photos themselves.

---

## Open Questions for Client (resolve before coding)
1. Domain owned / preferred?
2. Service area — Manama only, or all of Bahrain?
3. Operating hours and lead time for bookings?
4. Payment methods accepted on-site (cash only? BenefitPay? card reader?)
5. Are the "discounted" prices permanent or a launch promo?
6. Do they want pure WhatsApp flow, or also a booking form that captures customer details to a database/sheet?
7. Number of years in business / number of cars cleaned (for trust signals)?
8. Do they have professional photos, or only the iPhone shots seen so far? (Affects hero quality.)
9. Reviews / testimonials — Google reviews? Word of mouth only?
10. Logo source files (SVG, AI, PSD)? The PNGs we have are low-resolution.

---

## Reusable Skills & Agents from Other Projects

> ⚠️ **Note on the original brief:** The request was to "look at my other DEV files on my Mac and take all the used skills and agents." This pattern doesn't work cleanly in Claude Code:
>
> - CLAUDE.md is static context — it can't dynamically scan arbitrary directories at runtime.
> - The clean way to handle truly reusable skills/agents is to put them in **`~/.claude/agents/`** and **`~/.claude/skills/`**, where Claude Code picks them up globally for every project automatically. No per-project linking needed.
> - For project-specific skills you want shared between this project and another, list the **explicit paths** below. Claude Code can then read them when relevant.
>
> **Action required from user:** Either move shared skills/agents into `~/.claude/` (preferred), or fill in explicit paths in the block below.

### Skills/agents to reference (fill in)
```
TODO — list explicit paths or copy files into this project's .claude/ folder.

Example:
- ~/Dev/project-name/.claude/agents/frontend-builder.md
- ~/Dev/project-name/.claude/skills/tailwind-component-library/SKILL.md
- ~/Dev/project-name/.claude/skills/i18n-arabic-rtl/SKILL.md
```

### Project-local skills/agents
Once the user provides the paths, copy the relevant files into:
- `.claude/agents/` (this project's local agents)
- `.claude/skills/` (this project's local skills)

Then list them here for quick reference.

---

## Working Notes for Claude Code

- This is a small marketing site. **Do not over-engineer.** No Redux, no monorepo, no microservices.
- The single most important conversion event is the WhatsApp click. Instrument it.
- Test RTL on every screen before considering a feature done — it's the #1 thing that gets broken in bilingual sites.
- The before/after gallery is the conversion driver after the hero — invest design effort there, not in fancy hero animations.
- When unsure about copy, default to the client's existing tone (friendly, simple) rather than corporate detailing-shop language.