# Phase 5 — Behavioral & Mocks Tutorial Style Spec (MANDATORY)

You are writing ONE tutorial page for an existing HTML course. Voice and markup must match the rest of
the site. Read `phase5-behavioral/index.html` (the curriculum — your card is the contract for what you
must cover) and skim a completed sibling from another phase for the shared markup — e.g.
`phase4-system-design/06-caching-queues-resilience.html` — for the `.toc`, callout, and `details.qa`
patterns and the page skeleton. Copy that MARKUP and VOICE, not its topic structure.

## Audience
One reader: a React developer, 7 years experience, pivoting to full-stack. Frontend expert, decent
Java/Spring/Postgres and DSA now. Targeting **both** FAANG-grade values loops (Amazon Leadership
Principles, Meta, Google) and enterprise/fintech (Optum, JPMC, Goldman). Positioning already agreed:
he is a **senior 7-YOE engineer, frontend-expert, with strong current Java/Spring backend — he must
NOT over-claim 7 years of Java.** Honour that in every story and pitch. At 7 YOE he is graded on
ownership, judgment, influence and impact — not on effort.

## Voice
- Second person ("you"), confident, dense, zero filler. No "In this section we will…".
- **Teach the signal, not a script.** Never hand him lines to memorize robotically. Teach what each
  question tests, then give a model answer *shape* he adapts. Say out loud the exact framing sentences
  — that is the product — but always as a template to personalize.
- Be honest about what's rarely asked; mark awareness-level material as such.
- Connect to his real material (React, design systems, performance, a shipped product, mentoring) so
  the model stories are believable for HIM specifically.

## Model stories — the honesty rule (IMPORTANT)
The worked STAR stories you write are **templates in the correct shape, for him to swap his real
project into** — never fabrications he should claim verbatim. Make this explicit on the page at least
once (e.g. a `.note`: "This is the shape, not your script — drop your real project into this skeleton
and keep the structure."). Base them on plausible senior-frontend/full-stack situations (a design-system
rollout, a Core Web Vitals push, a risky migration, a production incident, a disagreement with a PM
over scope, mentoring juniors, an API contract fight with backend). Invent realistic but ROUND metrics
and flag them as placeholders to replace with his real numbers. Never imply he must state something untrue.

## Page skeleton (same as the rest of the site)
```
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>NN — Topic | Interview Prep</title>
<link rel="stylesheet" href="styles.css">
</head>
<body>
<header class="site-header">
  <div class="container">
    <div class="breadcrumb"><a href="index.html">← Course Home</a></div>
    <h1>NN — Topic</h1>
    <p>One-line hook.</p>
  </div>
</header>
<main class="container">
  <section><h2>Why this matters in the interview</h2> ...2 meaty paragraphs... </section>
  <div class="toc"><strong>On this page</strong><ul>...link every h2...</ul></div>
  ... body sections (see below) ...
  <section><h2 id="qa">Interview Q&amp;A</h2> 8-12 <details class="qa"> </section>
  <section><h2 id="takeaways">What to remember</h2> the compressed recall list </section>
  <nav class="page-nav"><a href="PREV.html">← NN−1 — Prev</a><a href="NEXT.html">NN+1 — Next →</a></nav>
</main>
</body>
</html>
```
Both nav slots always present. Page 01's left slot points to `index.html`; page 08's right slot points to `index.html`.

## Body structure — METHOD & DRILL pages (01, 02, 07, 08)
Concept-driven. Per concept: what it is → why it matters / what it's testing → how to do it (with a
concrete example or a filled-in template) → the pitfall → the say-it-out-loud line. Use `<table>` heavily
for things he'll revise from: the STAR anatomy, the story-bank matrix (story × theme), the 16 Amazon LPs
→ question → which story, delivery do/don't. For page 08's mock bank and page 07's LP list, a long
`<details class="qa">` bank is the right form (question in `<summary>`, what-it-tests + how-to-attack in the body).

## Body structure — ARCHETYPE pages (03, 04, 05, 06)
For each question theme in the card:
1. `<h2>` the theme. Open with **the questions in this family** (a short list of the real phrasings).
2. **What the interviewer is actually testing** — the signal behind the question.
3. **The trap** — the specific wrong turn (use `<div class="pitfall">`): badmouthing, being the lone hero,
   no resolution, "we" with no "I", a failure that's secretly a humblebrag or is genuinely disqualifying.
4. **2–3 fully-worked STAR model answers** — write them out in full, labelled Situation / Task / Action /
   Result, believable for a senior frontend→full-stack engineer, with round placeholder metrics. Use a
   styled block (a `<div class="note">` or a `<pre>`/`<blockquote>`-style container that exists in the
   stylesheet) so the story reads as a set piece.
5. **The follow-up drill** — the "what would you do differently / what did you learn" the interviewer
   always asks next, and how to answer it.
6. **Say it out loud** (`<div class="senior">`) — the one framing sentence that reads as senior.
7. **Maps to** — which company values / Amazon LPs this theme satisfies.

## Callouts — use them, don't overuse them (one per major section, never two in a row)
- `<div class="pitfall">` the specific wrong turn candidates take. Concrete, not generic.
- `<div class="note">` a useful aside, a real-world anchor, or the "this is a template not a script" reminder.
- `<div class="senior">` the say-it-out-loud line that a 7-YOE candidate delivers and a 3-YOE doesn't.
  This is the highest-value callout — earn it.

## Code / tables
- This phase is mostly prose and tables, not code. No syntax highlighting needed unless you show a
  filled-in template. If you DO use `<pre>`, HTML-escape every `<` `>` `&&` as `&lt;` `&gt;` `&amp;&amp;`.
- Lean on `<table>` for every comparison and every matrix — those are the night-before revision surface.

## Non-negotiables
- Cover everything named on this tutorial's index.html card. Nothing dropped.
- The page must be **complete and closed** — `</main></body></html>`. Last section as deep as the first.
- Self-contained: no CDN, no JS, no images. Only `styles.css`, which exists — do not modify it.
- **WRITE INCREMENTALLY.** Write head/intro/toc/first section, then Edit to append one section at a
  time (~8–12 Edits). Emitting a whole ~80KB page in one tool call will stall and die mid-stream.
  Verify at the end that the file ends with `</html>` and both nav slots exist.
