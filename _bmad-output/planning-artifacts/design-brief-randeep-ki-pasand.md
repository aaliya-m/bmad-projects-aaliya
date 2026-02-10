# Design Brief — "Randeep ki Pasand" Feature

**Date:** 2026-02-10
**Author:** Developer
**PRD Reference:** `_bmad-output/planning-artifacts/prd.md`
**Status:** Draft

---

## 1. Overview

Design the UI for "Randeep ki Pasand" — a curated content recommendation feature for Stage OTT's mobile web experience. This feature bridges the gap between trial signup (driven by Randeep Hooda ads) and first content play by presenting celebrity-curated regional content picks.

**Two screens to design:**
- **Variant A:** Enhanced post-trial payment success screen + homepage drawer
- **Variant B:** "Randeep ki Pasand" section on homepage for returning users

---

## 2. Design System Reference

> **Figma File:** https://www.figma.com/design/zr5WpG31m1eRom3SvlMyjc/Activation?node-id=0-1&t=7HpBYqbD5wrqZ2MQ-1
> **HTML Mockups:** `designs/randeep-ki-pasand-mockup.html` (open in browser to preview)
>
> All designs MUST use Stage's existing design system — colors, typography, spacing, component patterns, and visual language. Do not introduce new design patterns unless explicitly required by this brief.

### Key Design System Elements to Use
- Stage brand colors and gradients
- Existing card/tile components for content thumbnails
- Standard CTA button styles
- Bottom sheet/drawer patterns (if existing)
- Typography scale for Hindi/regional language text
- Existing play button iconography

---

## 3. Design Targets

| Attribute | Requirement |
|-----------|-------------|
| **Platform** | Mobile web only (320px–428px viewport) |
| **Browsers** | Instagram in-app, Facebook in-app, Chrome, Samsung Internet |
| **Orientation** | Portrait only |
| **Languages** | Hindi, Haryanvi, Rajasthani, Bhojpuri, Gujarati (text must not break layout) |
| **Accessibility** | Minimum 4.5:1 contrast ratio; tap targets ≥ 44px |
| **Performance** | Images < 50KB each (WebP); minimal DOM complexity |

---

## 4. Screen Designs Required

### 4A. Post-Trial Payment Success Screen (Variant A)

**Context:** User just paid ₹1 for a 7-day trial inside an in-app browser. This replaces the current static "payment done + trial ka maza lo" screen.

**Layout (top to bottom):**

```
┌─────────────────────────────┐
│                             │
│     ✅ Payment Successful   │
│     ₹1 Trial Activated      │
│                             │
│  ┌───────────────────────┐  │
│  │  [Randeep Hooda img]  │  │
│  │                       │  │
│  │  "Maine ye 3 movies   │  │
│  │   dekhi, maza aa      │  │
│  │   gaya!"              │  │
│  └───────────────────────┘  │
│                             │
│  ┌───────────────────────┐  │
│  │   ▶ Start Watching    │  │ ← Primary CTA (full width)
│  └───────────────────────┘  │
│                             │
│    7 days free trial active │ ← Subtle trial reminder
│                             │
└─────────────────────────────┘
```

**Design Notes:**
- **Randeep's image:** Use an approved brand ambassador photo asset. Warm, inviting expression. Cropped as a card or circular avatar — follow existing Stage image treatment patterns.
- **Quote text:** Regional language variants needed. Use Stage's body font at a comfortable reading size. The quote should feel personal, like Randeep is talking directly to the user.
- **"Start Watching" CTA:** Use Stage's primary action button style. High contrast. Full-width or near full-width. This is the ONLY action on the screen — no competing elements.
- **No distractions:** No app download prompts, no navigation bar, no hamburger menu. The entire screen funnels to one action.
- **Success indicator:** The checkmark/payment confirmation should be visible but NOT dominant — it's context, not the focus. The Randeep recommendation block is the hero.

**Interaction:**
- Tapping "Start Watching" navigates to homepage and auto-opens the "Randeep ki Pasand" drawer (see 4B).

---

### 4B. "Randeep ki Pasand" Drawer / Bottom Sheet (Variant A — Post-Trial)

**Context:** User tapped "Start Watching" on the success screen. Homepage loads with this drawer auto-opened over it.

**Layout:**

```
┌─────────────────────────────┐
│  [Homepage dimmed behind]    │
│                             │
│  ┌───────────────────────┐  │
│  │ ─── drag handle ───   │  │
│  │                       │  │
│  │ [Randeep img] Randeep │  │
│  │              ki Pasand│  │
│  │                       │  │
│  │ ┌─────┐ ┌─────┐ ┌────┤  │
│  │ │poster│ │poster│ │post│  │ ← Horizontal scroll of 3 cards
│  │ │     │ │     │ │    │  │
│  │ │Title │ │Title │ │Titl│  │
│  │ │[HAR] │ │[RAJ] │ │[BH]│  │ ← Language badge
│  │ │ ▶Play│ │ ▶Play│ │ ▶Pl│  │
│  │ └─────┘ └─────┘ └────┘  │
│  │                       │  │
│  │  See All Randeep's Picks →│
│  └───────────────────────┘  │
└─────────────────────────────┘
```

**Design Notes:**
- **Drawer:** Standard bottom sheet pattern. ~60% screen height. Rounded top corners. Drag handle at top. Background: dimmed homepage.
- **Header:** Randeep's small avatar/image + "Randeep ki Pasand" title. Use Stage's section header typography.
- **Content cards (3 visible):**
  - Poster thumbnail (vertical, 2:3 ratio) — optimized WebP
  - Title text below poster (1-2 lines, truncate with ellipsis)
  - Language badge (e.g., "HAR" for Haryanvi) — small pill/tag using Stage's badge component
  - **"▶ Play" button** — prominent, overlaid on poster bottom or below title. Use Stage's play button style. Tap target ≥ 44px.
- **Horizontal scroll:** Cards scroll horizontally. Peek of third card visible to indicate scrollability.
- **"See All" link:** Bottom of drawer. Text link with arrow. Navigates to a full-page "Randeep ki Pasand" collection.
- **Dismiss:** Swipe down or tap dimmed background area.

---

### 4C. "Randeep ki Pasand" Homepage Section (Variant B — Returning User)

**Context:** Returning trial or subscribed user visits the Stage homepage. This is an inline section, NOT a drawer.

**Layout:**

```
┌─────────────────────────────┐
│  [Stage header/nav]          │
│                             │
│  [Hero banner / carousel]    │
│                             │
│  ── Randeep ki Pasand ───── │ ← Section header with Randeep avatar
│                             │
│  ┌─────┐ ┌─────┐ ┌─────┐   │
│  │poster│ │poster│ │poster│  │ ← Horizontal scroll, 3-6 cards
│  │     │ │     │ │     │   │
│  │Title │ │Title │ │Title │  │
│  │ ▶Play│ │ ▶Play│ │ ▶Play│  │
│  └─────┘ └─────┘ └─────┘   │
│                             │
│  [Continue Watching]         │ ← Existing homepage sections continue
│  [Trending Now]              │
│  ...                        │
└─────────────────────────────┘
```

**Design Notes:**
- **Placement:** Immediately below the hero banner, ABOVE other content rows. This is the first content section the returning user sees.
- **Section header:** Small Randeep avatar (circular, ~32px) + "Randeep ki Pasand" text. Match existing Stage section header style. Optional: "Randeep ne recommend kiya" subtitle in lighter text.
- **Content cards:** Same card design as 4B but in a standard homepage content row. Horizontal scroll. 3-6 titles.
- **Consistency:** This section must look like a native part of the Stage homepage — same card sizes, spacing, and interaction patterns as existing content rows (e.g., "Trending Now", "New Releases").
- **Badge (optional P1):** Small "Randeep's Pick" badge on each poster — a small branded tag in the corner.

---

## 5. Content Card Component Spec

Design a reusable content card for both the drawer and homepage section:

```
┌──────────────┐
│              │
│   [Poster]   │  ← 2:3 ratio, rounded corners (match existing)
│   [WebP img] │
│              │
│  ▶ Play      │  ← Overlay button on poster (bottom-center)
│              │
├──────────────┤
│ Title Text   │  ← 1-2 lines, Stage body font, ellipsis overflow
│ [HAR] · 1h42 │  ← Language badge + duration, secondary text color
└──────────────┘
```

**States:**
- **Default:** As shown above
- **Pressed/Active:** Slight scale-down (0.97) + opacity change for tap feedback
- **Loading:** Skeleton shimmer placeholder matching card dimensions

---

## 6. Regional Language Copy

Provide localized copy for Randeep's recommendation message on the success screen:

| Language | Quote (Success Screen) | Section Title |
|----------|----------------------|---------------|
| Hindi (default) | "Maine ye 3 movies dekhi, maza aa gaya!" | Randeep ki Pasand |
| Haryanvi | "Maine ye 3 movies dekhi, maza aa gaya!" | Randeep ki Pasand |
| Rajasthani | "Maine ye 3 movies dekhi, maza aa gayo!" | Randeep ki Pasand |
| Bhojpuri | "Hum ye 3 movies dekhani, maza aa gail!" | Randeep ki Pasand |
| Gujarati | "Me aa 3 movies joi, maja aavi gayi!" | Randeep ni Pasand |

> **Note to copywriter:** These are placeholder translations. Please get native-speaker reviewed copy for each dialect. The tone should be casual, warm, and feel like a friend recommending something — not a formal endorsement.

---

## 7. Randeep Hooda Asset Requirements

| Asset | Format | Size | Usage |
|-------|--------|------|-------|
| Hero photo (success screen) | WebP/PNG | ~300x400px | Payment success recommendation card |
| Circular avatar (small) | WebP/PNG | 64x64px @2x | Drawer header, section header |
| Transparent cutout (optional) | PNG with alpha | ~500px wide | For more dynamic success screen layout |

> **Direction:** Warm, approachable expression. Casual/relatable feel — NOT a formal movie poster pose. Think: Randeep as your friend who watches regional content, not Randeep the Bollywood star.

---

## 8. Interaction & Animation

| Interaction | Behavior |
|-------------|----------|
| Drawer open (Variant A) | Slide up from bottom, 300ms ease-out. Homepage dims to 50% opacity behind. |
| Drawer dismiss | Swipe down gesture or tap dimmed area. Slide down 200ms. |
| Card tap (Play) | Scale down to 0.97 for 100ms, then navigate to player. |
| Horizontal scroll | Standard momentum scroll. Snap to card edges (scroll-snap). |
| Content loading | Skeleton shimmer on poster + text placeholders until images load. |

**Performance constraint:** Keep animations to `transform` and `opacity` only (GPU-accelerated). No layout-triggering animations.

---

## 9. A/B Test Visual Requirements

The design must support an A/B test toggle:

- **Control group:** See the current payment success screen (no changes)
- **Treatment group:** See the new enhanced success screen + "Randeep ki Pasand" drawer

The section on the homepage (Variant B) should also be toggleable. Design both the "on" and "off" states — the "off" state is simply the existing homepage without the Randeep section.

---

## 10. Deliverables Checklist

- [ ] Payment success screen (Variant A) — mobile web, 375px width
- [ ] "Randeep ki Pasand" drawer (Variant A) — over homepage
- [ ] Homepage section (Variant B) — inline with existing content rows
- [ ] Content card component — all states (default, pressed, loading)
- [ ] Language badge variants (HAR, RAJ, BHO, GUJ, HIN)
- [ ] Responsive adjustments for 320px and 428px viewports
- [ ] Dark mode adaptation (if Stage supports dark mode on web)
- [ ] Skeleton/loading states for all components
- [ ] Annotated specs with exact spacing, font sizes, and colors from Stage design system
