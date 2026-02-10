---
stepsCompleted: ['step-01-init', 'step-02-discovery', 'step-03-success', 'step-04-journeys', 'step-05-domain', 'step-06-innovation', 'step-07-project-type', 'step-08-scoping', 'step-09-functional', 'step-10-nonfunctional', 'step-11-polish']
inputDocuments: ['_bmad-output/brainstorming/brainstorming-session-2026-02-06.md']
workflowType: 'prd'
documentCounts:
  briefs: 0
  research: 0
  brainstorming: 1
  projectDocs: 0
---

# Product Requirements Document — "Randeep ki Pasand" Feature

**Author:** Developer
**Date:** 2026-02-10
**Version:** 1.0
**Status:** Draft

---

## 1. Executive Summary

### Problem Statement

Stage OTT is acquiring trial users (₹1 for 7 days) via Meta and Google ad campaigns featuring brand ambassador Randeep Hooda. While traffic and trial conversions are healthy, **web content consumption start is critically low**. Trial users are not beginning to watch content on the mobile web, and most are not installing the app. The current post-trial success screen is a dead end — it shows a payment confirmation and a Randeep Hooda message ("trial ka maza lo") but provides no pathway into content.

### Proposed Solution

**"Randeep ki Pasand"** — A curated content recommendation feature leveraging brand ambassador Randeep Hooda's trust and recognition to bridge the gap between trial signup and first content play. The feature uses a pull-based strategy (not push) to naturally draw users into consuming content on the mobile web immediately after trial activation and on subsequent visits.

### Two Variants

| Variant | Trigger | Experience |
|---------|---------|------------|
| **A — Post-Trial Activation** | Immediately after ₹1 payment success | Contextual message + homepage drawer with Randeep's top 3 picks, play buttons, and "Start Watching" CTA |
| **B — Returning User** | Homepage visit for existing trial/subscribed users | Drawer or section on homepage showcasing Randeep's 3-6 favourite picks |

### Key Constraint

Randeep Hooda is a **brand ambassador only** — Stage does not have any Randeep Hooda movies or shows in its library. The feature positions him as a trusted curator/recommender of regional content, not as a content source.

---

## 2. Product Vision & Goals

### Vision

Transform the post-trial dead-end into a compelling, zero-friction content discovery moment that leverages celebrity trust to activate regional content consumption on mobile web.

### Primary Goals

| # | Goal | Success Metric | Target |
|---|------|---------------|--------|
| G1 | Increase web content consumption start rate for trial users | % of trial users who start watching within 24 hours | +15% uplift vs control |
| G2 | Reduce post-trial drop-off | Bounce rate on post-payment screen | -20% reduction |
| G3 | Increase average content consumption time for trial users | Minutes watched in first 7 days (web) | +25% uplift vs control |
| G4 | Validate pull-based engagement model | Click-through rate on "Randeep ki Pasand" section | >8% CTR |

### Non-Goals

- Driving app installs (this is explicitly a web-first feature)
- Replacing the existing homepage layout for non-trial users
- Creating new content or acquiring Randeep Hooda content
- Push notifications or intrusive prompts

---

## 3. Target Users

### Primary Persona: Regional Content Seeker

- **Demographics:** 18-35 years old, male-skewed, Hindi-belt and Gujarati regions
- **Behavior:** Acquired via Meta/Google ads, consuming in mobile in-app browsers (Instagram/Facebook/Chrome in-app browser)
- **Language:** Haryanvi, Rajasthani, Bhojpuri, or Gujarati (based on ad targeting)
- **Context:** Scrolling social media, saw Randeep Hooda ad, clicked through, paid ₹1 trial
- **Mental model:** Expects instant gratification similar to Instagram reels; competing with "back to Instagram" gravity
- **Key tension:** Paid ₹1 because of Randeep's credibility but the content library is regional — the feature must bridge this expectation gap

### User Segments

| Segment | Description | Variant |
|---------|-------------|---------|
| New trial user | Just completed ₹1 payment | Variant A (Post-Trial) |
| Returning trial user | Comes back to Stage web during trial period | Variant B (Returning User) |
| Subscribed user | Active subscriber visiting homepage | Variant B (Returning User) |

---

## 4. User Journeys

### Journey A: Post-Trial Activation (Variant A)

```
User sees Randeep ad on Instagram/Facebook
  → Taps ad → Opens Stage web in in-app browser
  → Lands on trial page → Pays ₹1
  → Payment success screen shows:
      "Payment Successful! ✅"
      + Randeep's image with: "Maine ye 3 movies dekhi, maza aa gaya!"
      + "Start Watching" CTA button
  → Taps "Start Watching"
  → Redirected to homepage with "Randeep ki Pasand" drawer auto-opened:
      - 3 curated regional titles with poster, title, language badge
      - Each has a prominent "▶ Play" button
      - "See All Randeep's Picks" link at bottom
  → Taps Play on any title
  → Content begins playing → SUCCESS: First content consumption achieved
```

**Critical UX Moments:**
- Payment success → content discovery must be < 2 taps
- Content must be in user's dialect (detected from ad campaign targeting)
- No pop-ups, no Play Store redirects, no interruptions

### Journey B: Returning User (Variant B)

```
User returns to Stage web (via bookmark, link, or ad retargeting)
  → Homepage loads
  → "Randeep ki Pasand" section visible above the fold or as an auto-opened drawer
      - 3-6 curated titles with posters and play buttons
      - Randeep's image/branding as section header
      - "Randeep ne recommend kiya" badge on each title
  → User taps any title
  → Content begins playing → SUCCESS: Content consumption
```

---

## 5. Functional Requirements

### FR-A: Post-Trial Success Screen Enhancement (Variant A)

| ID | Requirement | Priority |
|----|-------------|----------|
| FR-A1 | Replace current post-trial success screen static message with dynamic content recommendation block | P0 |
| FR-A2 | Display Randeep Hooda image/avatar with a personalized recommendation message in the user's regional language | P0 |
| FR-A3 | Show "Start Watching" primary CTA button below the recommendation message | P0 |
| FR-A4 | On "Start Watching" tap, navigate to homepage with "Randeep ki Pasand" drawer auto-opened | P0 |
| FR-A5 | Recommendation message must be localized: Hindi default, with Haryanvi/Rajasthani/Bhojpuri/Gujarati variants based on ad campaign language | P1 |
| FR-A6 | Track impression and click events on the success screen CTA | P0 |

### FR-B: "Randeep ki Pasand" Content Drawer/Section

| ID | Requirement | Priority |
|----|-------------|----------|
| FR-B1 | Display a drawer (bottom sheet) or dedicated section showing curated content picks | P0 |
| FR-B2 | Variant A: Show 3 titles in drawer; Variant B: Show 3-6 titles in section | P0 |
| FR-B3 | Each title card must display: poster thumbnail, title, language badge, duration, and prominent "▶ Play" button | P0 |
| FR-B4 | Randeep's image/branding as the drawer/section header with "Randeep ki Pasand" title | P0 |
| FR-B5 | "Randeep ne recommend kiya" badge or label on each content card | P1 |
| FR-B6 | Content must be filtered by user's language preference (detected from ad campaign UTM parameters or user profile) | P0 |
| FR-B7 | "See All Picks" link at the bottom of the drawer to expand to a full page view | P2 |
| FR-B8 | Tapping "▶ Play" immediately starts content playback in the web player — no intermediate screens | P0 |
| FR-B9 | Drawer auto-opens on homepage for Variant A (post-trial redirect); shows as section for Variant B (returning user) | P0 |
| FR-B10 | Drawer can be dismissed by swiping down or tapping outside | P1 |

### FR-C: Content Curation (Backend/CMS)

| ID | Requirement | Priority |
|----|-------------|----------|
| FR-C1 | CMS interface for editorial team to curate "Randeep ki Pasand" content list per language | P0 |
| FR-C2 | Support separate curated lists per language: Haryanvi, Rajasthani, Bhojpuri, Gujarati, Hindi | P0 |
| FR-C3 | Each curated list supports 3-10 titles with manual ordering | P1 |
| FR-C4 | CMS must allow scheduling: set start/end dates for curated lists (for rotation/freshness) | P2 |
| FR-C5 | Fallback: If no curated list exists for a language, show "Most Popular" content in that language | P1 |

### FR-D: Analytics & Tracking

| ID | Requirement | Priority |
|----|-------------|----------|
| FR-D1 | Track impression events for "Randeep ki Pasand" section/drawer | P0 |
| FR-D2 | Track click events on each content card (title, position, language) | P0 |
| FR-D3 | Track "Start Watching" CTA click on post-trial success screen | P0 |
| FR-D4 | Track content play start events attributed to "Randeep ki Pasand" | P0 |
| FR-D5 | Track drawer dismiss events (Variant A) | P1 |
| FR-D6 | A/B test framework: ability to show/hide the feature for control group | P0 |

---

## 6. Non-Functional Requirements

| ID | Requirement | Target |
|----|-------------|--------|
| NFR-1 | Post-trial success screen must load in < 2 seconds on 3G connections | < 2s LCP |
| NFR-2 | "Randeep ki Pasand" drawer/section must render within 1 second of homepage load | < 1s render |
| NFR-3 | Content poster images must be optimized for mobile web (WebP, < 50KB each) | < 50KB |
| NFR-4 | Feature must work in Instagram in-app browser, Facebook in-app browser, Chrome, and Samsung Internet | All major mobile browsers |
| NFR-5 | No pop-ups, Play Store redirects, or app download prompts during the post-trial → first play journey | Zero interruptions |
| NFR-6 | Video playback must start within 3 seconds on 3G with adaptive bitrate | < 3s time-to-play |
| NFR-7 | Feature must support RTL text rendering for applicable regional languages | RTL support |
| NFR-8 | Randeep's image assets must be served via CDN with proper caching (7-day cache) | CDN cached |

---

## 7. Scope & Phasing

### Phase 1 — MVP (Target: 2-3 weeks)

- FR-A1 through FR-A4: Enhanced post-trial success screen with "Start Watching" CTA
- FR-B1 through FR-B4, FR-B8, FR-B9: Core drawer with 3 titles and play functionality
- FR-C1, FR-C2: Basic CMS curation per language
- FR-D1 through FR-D4, FR-D6: Core analytics and A/B test capability
- NFR-1 through NFR-6: Performance and compatibility requirements

### Phase 2 — Enhanced (Target: 2 weeks after MVP)

- FR-A5: Regional language localization of recommendation message
- FR-B5, FR-B6, FR-B7, FR-B10: Language filtering, badges, "See All", dismiss behavior
- FR-C3, FR-C5: Manual ordering and fallback logic
- FR-D5: Dismiss tracking

### Phase 3 — Optimization (Ongoing)

- FR-C4: Scheduled list rotation
- NFR-7, NFR-8: RTL support and CDN optimization
- Performance tuning based on real-world data
- Personalization: Algorithm-driven picks based on viewing history (replaces static curation)

---

## 8. A/B Testing Strategy

### Experiment Design

| Group | Experience | % Traffic |
|-------|-----------|-----------|
| Control | Current post-trial success screen (static message + "trial ka maza lo") | 50% |
| Treatment | Enhanced success screen with "Start Watching" CTA → "Randeep ki Pasand" drawer | 50% |

### Primary Metric
- **Content play start rate** within 24 hours of trial activation

### Secondary Metrics
- Post-trial success screen bounce rate
- Click-through rate on "Randeep ki Pasand" content cards
- Minutes watched in first 7 days
- Trial-to-subscription conversion rate (long-term)

### Statistical Requirements
- Minimum 1,000 users per variant before reading results
- 95% confidence level
- Minimum 7-day observation window

---

## 9. Technical Considerations

### In-App Browser Constraints
- Instagram and Facebook in-app browsers have limited JavaScript support and restricted popup/redirect behavior
- Video autoplay is restricted — require user tap to initiate playback
- Deep linking from in-app browsers is unreliable — keep entire experience within the web view
- Service workers may not be supported — cannot rely on PWA features

### Language Detection
- Primary: UTM parameters from ad campaigns (e.g., `utm_language=haryanvi`)
- Secondary: User profile language preference (if registered)
- Fallback: Hindi content as default

### Content Delivery
- Poster images: WebP format, multiple sizes for responsive loading
- Video: Adaptive bitrate streaming (HLS), start at lowest quality for fast time-to-play
- CDN: All static assets (Randeep images, posters) cached at edge

---

## 10. Dependencies & Risks

### Dependencies

| Dependency | Owner | Status |
|-----------|-------|--------|
| Randeep Hooda image/video assets for the recommendation message | Marketing/Brand team | Needed |
| CMS update to support "Randeep ki Pasand" curated lists | Backend/CMS team | To be built |
| UTM parameter standardization across all ad campaigns | Performance Marketing | To be verified |
| Web video player stability in in-app browsers | Engineering | To be tested |

### Risks

| Risk | Impact | Mitigation |
|------|--------|-----------|
| Users feel "bait and switch" — clicked for Randeep, get regional content | High | Position Randeep as recommender, not content source. Messaging: "Randeep ki pasand" not "Randeep ki film" |
| In-app browser video playback issues | High | Extensive testing on top 5 in-app browsers; fallback to poster + "tap to play" if autoplay fails |
| Low content quality perception after celebrity-grade ad | Medium | Curate only the highest-quality titles for the "Randeep ki Pasand" list |
| Ad campaign UTM parameters inconsistent for language detection | Medium | Implement fallback chain: UTM → profile → device language → Hindi default |

---

## 11. Success Criteria

### Launch Criteria (Go/No-Go)
- [ ] Post-trial success screen loads < 2s on 3G in Instagram in-app browser
- [ ] "Randeep ki Pasand" drawer displays correctly with 3 titles in all supported languages
- [ ] Content play starts within 3 seconds of tap
- [ ] Zero pop-ups or Play Store redirects in the trial → first play flow
- [ ] A/B test framework verified with correct traffic split
- [ ] Analytics events firing correctly for all tracked interactions

### Feature Success (4-week evaluation)
- Content play start rate: +15% uplift vs control
- Post-trial bounce rate: -20% reduction
- "Randeep ki Pasand" CTR: >8%
- No negative impact on trial-to-subscription conversion

---

## Appendix A: Brainstorming Origin

This PRD emerged from a brainstorming session (2026-02-06) focused on improving Stage OTT web consumption for trial users. Key validated concepts that informed this feature:

1. **Celebrity as Curator** — Bridging the expectation gap between celebrity ads and regional content
2. **Zero-Tap Content Discovery** — Eliminating the dead-end post-trial screen
3. **Reel-like Engagement Model** — Competing with Instagram's effort-to-dopamine ratio
4. **Kill the Friction** — Removing pop-ups and Play Store redirects from the web trial flow
5. **Dialect-First Personalization** — Showing content in the user's specific language, not generic Hindi
