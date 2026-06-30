# Hub Redesign Brief — make it stop looking AI-generated

**How to use this doc:** hand it to a design pass (e.g. `claude design`) together with the current
`index.html` + `styles.css`. It defines the *intent, constraints, and wireframe skeleton* — not the
final visuals. The designer fills in the type system, palette, spacing, and motion. **All project
copy and metrics already exist** in `index.html` and each repo's README; reuse them verbatim
(see "Honesty constraint").

---

## 1. Who this is for & the 10-second job

- **Audience:** data-science hiring managers + recruiters at Capital One, JPM, Bloomberg, Microsoft,
  Meta, Deloitte. Many open it on a phone, between other tabs, for ~10 seconds.
- **The one job:** in 10 seconds, convey *"this person ships real, measured DS work"* and pull a
  click into 1–2 live demos. Everything serves that. If an element doesn't earn the click or build
  credibility, cut it.

## 2. The "AI-slop" look to avoid (and why)

These are the tells that make a portfolio read as generated. **Do not ship any of them:**

- ❌ A flat 3-column grid where **every card has identical visual weight** → nothing signals what's
  best. Real portfolios have hierarchy.
- ❌ **Indigo/purple gradient hero**, glassmorphism, neon glow, sparkle "✨" accents.
- ❌ **Emoji used as personality / section icons.** At most one, deliberately.
- ❌ Vague hero copy ("I build and ship interactive data & ML applications"). Say something only
  *this* person could say, backed by a number.
- ❌ Default **Inter/system-stack everything** at one size → no typographic voice.
- ❌ Centered everything, equal margins, no rhythm.
- ❌ **All-text cards** with no visual proof (this is why we're adding demo GIFs/thumbnails).
- ❌ Generic badges row that repeats "Python" on every card with no grouping.

## 3. North-star direction

Editorial, evidence-led, confident-but-restrained — closer to a well-designed case-study page or a
research lab site than a SaaS landing page. **One** signature element (a distinctive type treatment,
a structural asymmetry, or a single accent colour used sparingly) instead of many effects. Let
whitespace and real metrics do the work.

## 4. Hard constraints (must keep)

- **Tech:** stays plain **static HTML + CSS** (minimal JS ok). No React/Tailwind/build step — it's
  GitHub Pages (see `CLAUDE.md`). Mobile-first; **Lighthouse > 90**.
- **Honesty constraint:** every metric is copied verbatim from the project READMEs. **Invent
  nothing**, round nothing, add no metric that isn't already there.
- **Content exists:** 1 pinned project (StarCoder2), 11 portfolio projects (10 live, P6 Tableau is
  "in progress"). Keep all of them; the redesign is layout/visual, not new copy.
- **Personal data limit:** name, email, LinkedIn, GitHub, résumé only (per `CLAUDE.md`).
- **Performance:** demo GIFs are lazy-loaded; respect `prefers-reduced-motion` (swap GIF → static
  poster). Total page weight stays modest.

## 5. Information architecture (lead with proof, not prose)

Reorder the mental model from "list of projects" to **"ranked evidence."**

- Cards should **lead with the result/metric**, then a one-line what-it-is — not a 3-bullet
  Problem→Approach→Result wall. Move detail to the repo/README.
- Introduce **visual hierarchy by importance** (tiers below), so the eye lands on the strongest work
  first. Suggested tiering (from the hiring-visibility ranking):
  - **Spotlight (1–2):** Experimentation Lab (A/B testing) + Uplift Studio (causal).
  - **Primary (4–6):** Credit Risk, 10-K RAG, Model Monitor, Forecasting, Recsys, SQL Copilot.
  - **Secondary (rest):** Active Learning, SQL Workbench, StarCoder2 (pinned), HR Attrition.

## 6. Wireframe skeleton (boxes + intent — designer makes it real)

```
┌───────────────────────────────────────────────────────────────────────┐
│ HERO  (asymmetric, NOT centered)                                        │
│   Name — small, confident.  ONE sentence with a number, e.g.            │
│   "I ship measured ML: causal targeting, drift detection, honest        │
│    backtests — 11 live demos you can click."                            │
│   [ Résumé ]  [ LinkedIn ]  [ GitHub ]   ← restrained, not pill-soup    │
│   (optional) tiny "live status" line: "10 demos live now"               │
└───────────────────────────────────────────────────────────────────────┘

┌───────────────────────────── SPOTLIGHT ───────────────────────────────┐
│  Large featured card — wider than the grid. GIF/thumbnail LEFT,        │
│  metric headline RIGHT.  This is the first thing the eye hits.          │
│   [   ab-lab.gif   ] │  EXPERIMENTATION LAB · A/B Testing               │
│   [  720×450 loop  ] │  "peeking inflates FPR 5% → 25%"                 │
│                      │  one line · [ Live demo ] [ Code ]               │
│  (optionally a 2nd spotlight: Uplift Studio, same treatment mirrored)   │
└───────────────────────────────────────────────────────────────────────┘

┌──────────────────────────── PROJECT GRID ─────────────────────────────┐
│  Responsive grid, but NOT uniform — primary cards larger / accented.    │
│  ┌── card ─────────────┐  ┌── card ─────────────┐                       │
│  │ [media: gif/thumb]  │  │ [media or tint]     │   ← media slot top    │
│  │ TITLE      ·  tag   │  │ TITLE      ·  tag    │                       │
│  │ **metric headline** │  │ **metric headline**  │   ← lead with number  │
│  │ one-line what-it-is │  │ one-line what-it-is  │                       │
│  │ tech · tech · tech  │  │ tech · tech · tech   │   ← grouped, subtle   │
│  │ [Live] [Code]       │  │ [Live] [Code]        │                       │
│  └─────────────────────┘  └─────────────────────┘                       │
│  status: a quiet "Live / In progress" affordance, not a loud badge.     │
└───────────────────────────────────────────────────────────────────────┘

┌──────────────────────────────── FOOTER ───────────────────────────────┐
│  Built static on GitHub Pages · source link · one human line.          │
└───────────────────────────────────────────────────────────────────────┘
```

### Card anatomy (states to design)

- **Media slot** (top): demo GIF (lazy) OR a static thumbnail OR a tasteful colour/data tint if no
  media yet. Reduced-motion → poster image.
- **Hover:** subtle lift / accent edge — one effect, not three.
- **Status:** Live / In progress as a quiet dot or label, not a colored pill on every card.
- **"In progress" (HR Attrition):** visually de-emphasized but not broken-looking.

## 7. Design tokens for the designer to decide (with guardrails)

- **Type:** pick a real pairing (e.g. a characterful display/serif for headings + a clean grotesk for
  body) and a **modular scale** (don't set everything at 16px). Guardrail: legible, fast-loading
  (≤2 weights, self-host or system).
- **Colour:** restrained neutral base + **one** accent. No gradients-as-decoration. Ensure AA contrast.
- **Spacing:** define a scale and use generous, *rhythmic* whitespace. Asymmetry is welcome.
- **Motion:** ≤2 micro-interactions (hover, in-view reveal). Honor `prefers-reduced-motion`.

## 8. Responsive & accessibility

- Test at **375px** (single column, spotlight collapses gracefully, GIFs stay legible).
- Semantic landmarks, focus-visible states, alt text that states the *insight* (not "a gif"),
  keyboard-navigable cards, AA contrast.

## 9. Out of scope / don't touch

- Don't rewrite project copy or invent metrics. Don't add projects. Don't change URLs.
- Don't introduce a framework or build step. Don't add tracking/analytics.

## 10. Deliverables expected back

1. Updated `index.html` + `styles.css` (and a small `app.js` only if truly needed).
2. A short rationale: the type pairing, the accent, and the *one* signature move chosen.
3. Confirmation it passes: Lighthouse > 90, 375px check, reduced-motion check, AA contrast.

## Acceptance criteria (how we'll judge "not AI-slop")

- A stranger can name the **single strongest project** within 5 seconds (hierarchy works).
- At least the spotlight card leads with a **real metric + visual proof**, not three text bullets.
- None of the §2 tells are present.
- It still loads fast and works on a phone.
