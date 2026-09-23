# Dental Office Operations Control Room

Recruiter-facing case study route for Dylan Walls' portfolio: a calm, bounded walkthrough of how a messy dental-office workflow becomes a legible operating picture. This is a static review artifact, not a production dental application.

Live route: `https://outlaw-intelligence.github.io/dylan-walls-portfolio/dental-office-operations/`

## What this is

The route demonstrates a control-room experience and a four-step critical path:

```text
operations queue
  -> appointment / intake context
  -> clinical follow-up signal
  -> human review handoff
```

The walkthrough is browser-local. It uses deterministic synthetic values, has loading/empty/unavailable/success states, supports reset, and keeps the disconnected boundary explicit. It makes no network requests, writes no storage, submits no form, signs no note, changes no schedule, submits no claim, and processes no payment.

## Provenance

- Verified source project: `/Users/dylanwalls/workspace/dental-office-platform` (private local project; not published)
- UI reference worktree/branch: `.worktrees/integration-command-center` on `dental-command-center`
- Reference commit: `8c47c3d`
- Verified source behaviors at that ref: typed command-center projection; appointment/resource status; intake, clinical follow-up, and claim-readiness signals; explicit loading/empty/error states; synthetic-only and not-connected labels; exact-money representation in the source read model.
- This route is an adaptation, not a connected copy of the source application.

### Claim classes

| Class | Meaning in this artifact |
|---|---|
| Verified source behavior | Supported by the source project's code/tests at the reference commit. |
| Synthetic demo fixture | Fictional names, counts, statuses, and labels used to make the route inspectable. |
| Observed prototype | Behavior implemented and exercised in this static route, such as the local state machine and reset. |
| Proposed follow-up | A future integration seam; not implemented or claimed as production behavior. |

## Files in this route

- `index.html` — the case study page (self-contained: inline CSS/JS, no external assets)
- `data/claims.json` — machine-readable claim ledger mirroring the on-page ledger
- `README.md` — this file

## Run locally

```bash
# from the repository root
python3 -m http.server 4173
```

Open `http://127.0.0.1:4173/dental-office-operations/`.

The page is intentionally self-contained: no CDN fonts, remote scripts, analytics, external images, backend, or form endpoints.

## Publishing

The live site is served by GitHub Pages from the `main` branch of `Outlaw-Intelligence/dylan-walls-portfolio`. Changes to this route go live on merge to `main` (Pages deploy follows automatically).

## Verification notes

Static checks for this route:

- `main`, skip link, heading hierarchy, `#walkthrough`, and `#architecture` are present.
- Portfolio homepage contains one link to `dental-office-operations/`.
- Route contains no `fetch`, `XMLHttpRequest`, form action, storage write, or external asset request.
- Route exposes `data-action="advance"`, reset, loading, empty, error, and success states.
- CSS includes 44px control targets, visible focus, reduced-motion handling, and mobile containment.

Browser verification:

1. Open the route.
2. Activate **Run the walkthrough**.
3. Exercise the four states in order and confirm the final handoff says human approval is required.
4. Exercise **Reset walkthrough**, **Empty queue**, **Unavailable source**, and **Loading read-model**.
5. At approximately 390px wide, confirm no page-level horizontal overflow and that the action controls remain reachable by keyboard.
6. Check the browser console for errors.

## Changelog

- 2026-09-23 — design polish pass:
  - Layout rhythm systematized: spacing scale, consistent section padding, eyebrow/heading/intro gaps, and card/note/table padding unified.
  - Hero: soft radial wash behind the preview, italic serif accent in the headline, larger CTA buttons with arrow nudge on hover, refined fact grid.
  - Window chrome (traffic-dot title bars) on the hero preview and the walkthrough shell; hero preview gets a hover lift and gradient throughput bars.
  - Scroll reveal on cards, figures, notes, accordions, table, and next-step items — staggered, JS-gated, and fully disabled under `prefers-reduced-motion`.
  - Walkthrough progress bar now shows a continuous fill; current-step top tick replaced by the fill.
  - Architecture figure gains an observed/proposed legend and soft node shadows.
  - Evidence accordions get custom plus/minus disclosure markers; claim table gets a tinted header and emphasized claim column.
  - Footer rebuilt with brand lockup, synthetic-data badge, portfolio link, and back-to-top.
  - Sticky topbar gains a shadow once scrolled; anchored sections clear the sticky bar.
  - README rewritten: removed stale worktree/assignment language, documented the GitHub Pages publishing path.
- 2026-09-23 — external audit fixes and visual refresh:
  - Architecture diagram: dashed "proposed" flows now use the amber arrowhead via CSS (`marker-end` on `.flow-proposed`); previously the teal `.flow` rule overrode the presentation attribute.
  - Reduced motion: the walkthrough launcher now honors `prefers-reduced-motion` for programmatic scrolling instead of forcing smooth scroll.
  - Touch targets: all interactive controls are now 44px minimum (`.button-small` and state-lab buttons raised from 40px/36px).
  - Badge lanes: walkthrough record badges use a neutral `.badge-record` style; only severity (`HIGH`) keeps the amber synthetic badge. Fixture values no longer borrow the green "verified source behavior" lane.
  - Added a `<noscript>` fallback that hides the interactive demo shell and explains the walkthrough needs JavaScript.
  - Topbar navigation links now remain visible on small screens (only the decorative label collapses).
  - Visual refresh: sticky blurred topbar, hero throughput strip, button/card hover lifts, progress-step current indicator, step fade transitions, table row hover, rounded panels, `::selection` tint, tabular numerals.
