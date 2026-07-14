# Resume notes — where the course build stopped

Last updated: 2026-07-14

## Status

| Phase | State |
|---|---|
| Phase 1 — Java/Spring/Postgres | Complete (16 tutorials, committed earlier) |
| Phase 2 — Frontend | Complete (18 tutorials, committed earlier) |
| Phase 3 — DSA | **Complete** — 14 tutorials, 144 problems, ~1.8 MB |
| Phase 4 — System Design | **18 of 27 done** — Blocks A + B complete (~2.2 MB) |

## Phase 4 — what's left (9 pages)

The curriculum, and the per-page contract for what each must cover, is already written in
`phase4-system-design/index.html`. Each card's description IS the spec — build to it.

**Block C — Frontend system design (5)**
- `19-frontend-method.html` — The Frontend System Design Method (RADIO)
- `20-feed-ui.html` — Design a News Feed UI
- `21-autocomplete.html` — Design an Autocomplete / Typeahead
- `22-design-system.html` — Design a Component Library / Design System
- `23-realtime-collab.html` — Design a Real-Time Collaborative UI

**Block D — Low-level design (2)**
- `24-lld-solid-patterns.html` — LLD in Java: SOLID & the patterns that show up
- `25-lld-case-studies.html` — Parking lot · elevator · BookMyShow

**Block E — Drills (2)**
- `26-estimation-drills.html` — Back-of-envelope estimation
- `27-tradeoff-flashcards.html` — Trade-off flashcards

Pages 19–22 were started and then deliberately deleted (they were 13–33 KB stubs against a
~100 KB target). Start them fresh; nothing of value was lost.

## How to build them

1. Read `.course-authoring/phase4-system-design-style.md` — the mandatory style spec. Foundations
   pages (19, 24, 26, 27) use the concept-driven structure; case studies (20–23, 25) use the
   10-section worked-transcript structure. **19 and 20–23 use RADIO, not the backend 10-section
   shape** — 19 establishes RADIO and 20–23 must visibly follow it.
2. Read a completed sibling for voice: `phase4-system-design/13-payments-orders.html` (case study)
   or `06-caching-queues-resilience.html` (foundations).
3. One subagent per page, run in parallel. **Tell each agent to WRITE INCREMENTALLY** (Write the
   head + first sections, then Edit to append one section at a time, ~8–12 edits). Agents that try
   to emit a 100 KB page in a single tool call stall and die mid-stream — this happened three times.

## When 19–27 land, undo the temporary link patches

To keep the shipped site free of dead links, pages 19–27 were disabled in the UI:
- `phase4-system-design/index.html` — cards for 19–27 have their `href` replaced with
  `href="#" onclick="return false" style="opacity:.5; cursor:default"`. **Restore the real hrefs.**
- 13 forward-references in the prose of pages 01–18 that pointed at 19/21/23 were de-linked
  (anchor stripped, text kept). Optional to restore; the text still reads correctly.
- `18-streaming-aggregation.html` page-nav right slot points at `index.html`. **Repoint it at
  `19-frontend-method.html`** once 19 exists.

## Verification (run before committing any new pages)

Every page must: end with `</html>`, have a `page-nav` with both slots, have no broken `#anchors`,
no dead cross-file links, and **no unescaped `<` or `&&` inside `<pre>` blocks** (the #1 corruption
source — it silently breaks the page). A node script that checks all of this is easy to re-derive;
`<strong>`/`<em>` inside `<pre>` are legitimate and should be whitelisted.

## Still outstanding beyond Phase 4

Phase 5 — behavioral/STAR + mocks — was in the original plan and has not been started.
