# Dental Office Operations Control Room

Recruiter-facing case study route for Dylan Walls' portfolio. This is a local static review artifact, not a production dental application.

## Scope

The route demonstrates a calm clinical-operations control-room experience and a bounded critical path:

```text
operations queue
  -> appointment / intake context
  -> clinical follow-up signal
  -> human review handoff
```

The walkthrough is browser-local. It uses deterministic synthetic values, has loading/empty/unavailable/success states, supports reset, and makes the disconnected boundary explicit. It does not make network requests, write to storage, submit a form, sign a note, change a schedule, submit a claim, or process a payment.

## Source of truth and provenance

- Verified source repository: `/Users/dylanwalls/workspace/dental-office-platform`
- UI reference worktree: `/Users/dylanwalls/workspace/dental-office-platform/.worktrees/integration-command-center`
- Reference commit: `8c47c3d`
- Relevant verified source behaviors: typed command-center projection; appointment/resource status; intake, clinical follow-up, and claim-readiness signals; explicit loading/empty/error states; synthetic-only and not-connected labels; exact-money representation in the source read model.
- The route is an adaptation, not a connected copy of the source application.
- `data/claims.json` is the machine-readable claim ledger. The visible page repeats the same distinction for recruiter review.

### Claim classes

| Class | Meaning in this artifact |
|---|---|
| Verified source behavior | Supported by the source project's code/tests at the reference worktree and commit. |
| Synthetic demo fixture | Fictional names, counts, statuses, and labels used to make the route inspectable. |
| Observed prototype | Behavior implemented and exercised in this static route, such as the local state machine and reset. |
| Proposed follow-up | A future integration seam; not implemented or claimed as production behavior. |

## Run locally

From the isolated portfolio worktree:

```bash
cd "/Users/dylanwalls/Documents/Outlaw Intelligence/Zeus/Projects/worktrees/dylan-portfolio-dental-case-study"
python3 -m http.server 4173
```

Open:

- `http://127.0.0.1:4173/` — portfolio homepage with the featured case-study link
- `http://127.0.0.1:4173/dental-office-operations/` — this route

The page is intentionally self-contained. It uses no CDN fonts, remote scripts, analytics, external image, backend, or form endpoint.

## Verification notes

Required checks for this bounded assignment:

```bash
git status --short --branch
git diff --stat
git diff --name-only
curl -fsS http://127.0.0.1:4173/
curl -fsS http://127.0.0.1:4173/dental-office-operations/
```

Static checks should confirm:

- `main`, skip link, heading hierarchy, `#walkthrough`, and `#architecture` are present.
- Homepage contains one link to `dental-office-operations/`.
- Route contains no `fetch`, `XMLHttpRequest`, form action, storage write, or external asset request.
- Route exposes `data-action="advance"`, reset, loading, empty, error, and success states.
- CSS includes 44px control targets, visible focus, reduced-motion handling, and mobile containment.

Browser verification boundary:

1. Open the route at the exact local HTTP URL.
2. Activate **Run the walkthrough**.
3. Exercise the four states in order and confirm the final handoff says human approval is required.
4. Exercise **Reset walkthrough**, **Empty queue**, **Unavailable source**, and **Loading read-model**.
5. At approximately 390px wide, confirm no page-level horizontal overflow and that the action controls remain reachable by keyboard.
6. Check the browser console for errors.

No deployment, commit, push, merge, analytics, outreach, or production mutation is part of this assignment.

## Allowed change set

The worktree root is the repository's `public` checkout. The only intended changed paths are:

- `index.html` — one featured case-study link
- `dental-office-operations/index.html`
- `dental-office-operations/data/claims.json`
- `dental-office-operations/README.md`

Rollback is the removal of this worktree/branch or reverting only these paths. The primary checkout remains untouched.
