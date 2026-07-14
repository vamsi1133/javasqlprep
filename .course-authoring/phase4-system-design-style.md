# Phase 4 — System Design Tutorial Style Spec (MANDATORY)

You are writing ONE tutorial page for an existing HTML course. Voice and markup must match the rest
of the site. Read `phase4-system-design/index.html` (the curriculum — your card is the contract for
what you must cover) and skim `phase3-dsa/04-stacks.html` (a completed sibling page — copy its VOICE
and its callout/Q&A markup, NOT its structure; system design pages are shaped differently).

## Audience
One reader: a React developer, 7 years experience, pivoting to full-stack. Strong frontend, decent
Java/Spring/Postgres (he just did a deep phase on it), decent DSA. Weak on distributed systems.
Targeting **both** FAANG-grade loops and enterprise/fintech (Optum, JPMC, Goldman). At 7 YOE he is
graded on **judgment and trade-offs**, not on knowing more boxes to draw.

## Voice
- Second person ("you"), confident, dense, zero filler. No "In this section we will…".
- **Teach judgment, not diagrams.** Never present a design as THE answer. Every choice is a
  trade-off, and the reader must learn to *derive* the design from the requirements.
- Constantly give him the exact sentence to **say out loud** in the interview. That is the product.
- Be honest about what's rarely asked. Mark awareness-level material as awareness-level and say so.
- Connect to what he knows (React, HTTP, Postgres, Spring) where genuinely apt — never forced.

## Page skeleton
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
Both nav slots always present. First page's left slot and last page's right slot point to `index.html`.

## Body structure — FOUNDATIONS pages (01-06, 19, 24, 26, 27)
Concept-driven. Per concept: what it is → **why it exists / what problem it solves** → how it works
(with a diagram or code) → **when you'd choose it and when you wouldn't** → the interview soundbite.
End every major concept with an explicit trade-off. Use `<table>` heavily for comparisons — SQL vs
NoSQL, L4 vs L7, B-tree vs LSM. Those tables are what he'll revise from the night before.

## Body structure — CASE STUDIES (07-18, 20-23, 25)
Each case study is a **worked transcript of a strong 45-minute answer**, in this order:
1. `<h2>1. The prompt</h2>` — the question as an interviewer would give it, deliberately vague.
2. `<h2>2. Requirements</h2>` — the clarifying questions to ask FIRST, with the answers you'd assume.
   Split **functional** vs **non-functional** explicitly. Nail the scope; say what you're cutting.
3. `<h2>3. Estimation</h2>` — real numbers. DAU → QPS → storage → bandwidth. Show the arithmetic.
   Round aggressively and say you're rounding. Then state which number actually drives the design
   (usually the read:write ratio, or storage, or fan-out) — that's the senior move.
4. `<h2>4. API design</h2>` — the handful of endpoints, request/response shapes.
5. `<h2>5. Data model</h2>` — tables/collections with fields; the access patterns that justify them;
   the SQL-vs-NoSQL decision made explicitly and defended.
6. `<h2>6. High-level design</h2>` — an ASCII/HTML box diagram (see below) + the request walkthrough,
   component by component, following one write and one read end to end.
7. `<h2>7. Deep dive: …</h2>` — ONE OR TWO sections on the thing the interviewer will actually push
   into. This is the heart of the page and where the archetype is taught. Name it explicitly:
   "This is where the interview really happens."
8. `<h2>8. Scaling &amp; bottlenecks</h2>` — what breaks first at 10×, and the fix. Be specific.
9. `<h2>9. Trade-offs</h2>` — a table of every real decision, the alternative, and when you'd flip.
10. `<h2>10. Follow-ups you should expect</h2>` — the real ones, with the answers.
Then the Q&A and takeaways sections.

## Diagrams — self-contained, no images
Use a `<pre>` box-drawing diagram. Keep it under ~76 chars wide so it doesn't scroll on mobile.
Example:
```
<pre><code>   Client ──▶ CDN ──▶ API Gateway ──▶ Service ──┬──▶ Cache (Redis)
                                                 │
                                                 └──▶ DB (Postgres)
</code></pre>
```
Label every arrow with what flows over it when it isn't obvious. Prefer 2-3 focused diagrams over one
giant unreadable one.

## Callouts — use them, don't overuse them
- `<div class="pitfall">` the specific wrong turn candidates take. Concrete, not generic.
- `<div class="note">` a useful aside or a real-world anchor.
- `<div class="senior">` the thing a 7-YOE candidate says that a 3-YOE candidate doesn't. Use these
  for the say-it-out-loud lines. This is the highest-value callout on the page — earn it.
Roughly one per major section, never two in a row.

## Code
- Only where it earns its place: schemas, API shapes, a key algorithm (consistent hashing ring,
  token bucket), config. **Java/SQL for backend pages, JS/TS for frontend pages.**
- Syntax-highlight by hand with the stylesheet's spans: `<span class="kw">` keywords ·
  `<span class="str">` strings · `<span class="com">` comments · `<span class="num">` numbers ·
  `<span class="typ">` types · `<span class="ann">` annotations.
- HTML-escape inside `<pre>`: `&lt;` `&gt;` `&amp;`. A raw `<` or `&&` in code WILL break the page —
  check every comparison operator and every arrow you draw. This is the #1 corruption source.

## Non-negotiables
- Cover everything named on this tutorial's index.html card. Nothing dropped.
- The page must be **complete and closed** — `</main></body></html>`. Never trail off. The last
  section gets the same depth as the first.
- Self-contained: no CDN, no JS, no images. Only `styles.css`, which exists — do not modify it.
- **WRITE INCREMENTALLY.** Write the file with head/intro/toc/first section, then Edit to append one
  section at a time (~8-12 Edits). Emitting a whole 100KB page in one tool call will stall and die.
  Verify at the end that the file ends with `</html>`.
