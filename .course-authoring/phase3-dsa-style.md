# Phase 3 DSA — Tutorial Style Spec (MANDATORY)

You are writing ONE tutorial page for an existing course. It must be indistinguishable in voice,
structure, and markup from the reference file `phase3-dsa/04-stacks.html`.

**BEFORE WRITING: Read `phase3-dsa/04-stacks.html` in full** (it is the gold-standard reference for
voice and markup) **and `phase3-dsa/index.html`** (the curriculum — your tutorial's card there is the
contract for exactly which problems you must cover; cover ALL of them, in that order).

## Audience
One reader: a React developer, 7 years experience, pivoting to full-stack. Strong JS, weak on
formal DSA. Targeting **enterprise-tier loops** — banks/fintech/healthcare/large product companies
(Optum, JPMC, Goldman Sachs and peers), plus some FAANG. He is graded on speed, clean code, and
narrating his thinking — not on exotic algorithms.

## Voice
- Second person ("you"), confident, dense, zero filler. No "In this section we will…" throat-clearing.
- Teach **recognition and derivation**, never memorization. The reader must be able to *rederive* the
  code under pressure. Constantly give him the exact sentence to **say out loud** in the interview.
- Connect to his existing frontend knowledge where it's genuinely apt (call stack, event loop,
  virtual DOM diffing, React reconciliation, memoization ≈ useMemo, debounce ≈ sliding window).
  Do NOT force it where it doesn't fit.
- Name-drop the enterprise tier (Optum/JPMC/Goldman) only where it's substantive — which problems
  actually get asked and why. Never as filler.

## Page skeleton (follow exactly)
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
    <p>One-line hook: what this pattern actually is.</p>
  </div>
</header>

<main class="container">
  <section><h2>Why interviewers ask this</h2> ...2 meaty paragraphs... </section>

  <div class="toc"><strong>On this page</strong><ul>...anchor links to every h2...</ul></div>

  <section><h2 id="recognize">1. Recognizing the pattern</h2>
    Bulleted list of trigger phrases in a problem statement that mean "use this pattern".
    Include at least one .senior callout with the say-it-out-loud recognition sentence.
  </section>

  <section><h2 id="template">2. The template(s)</h2>
    The reusable code skeleton, then a line-by-line breakdown as a <ul>, then the complexity
    argument spelled out (why it's O(n) and not O(n^2)), then a "knobs" <table> showing how the one
    template becomes every problem in the tutorial.
  </section>

  <section><h2 id="...">3..N. Problem sections</h2>
    Grouped by sub-pattern, in rising difficulty. Hard problems go LAST in a section titled
    "Stretch" and are labeled as rarely asked at this tier.
  </section>

  <section><h2 id="qa">Interview Q&amp;A</h2> 6-10 <details class="qa"> conceptual questions </section>
  <section><h2 id="drills">Re-solve drills</h2> the spaced-repetition plan </section>

  <nav class="page-nav">
    <a href="PREV.html">← NN−1 — Prev Topic</a>
    <a href="NEXT.html">NN+1 — Next Topic →</a>
  </nav>
</main>
</body>
</html>
```
(First tutorial: left nav slot is `<a href="index.html">← Course Home</a>`. Last tutorial: right slot
is `<a href="index.html">Course Home →</a>`. Both slots always present so flex spacing holds.)

## EVERY problem must have, in this order
1. `<h3>Problem Name (LC #NN) <span class="tier tier-3">EASY</span> ★</h3>`
   - tier-3 = EASY, tier-2 = MEDIUM, tier-1 = HARD. `★` only if it's a THE-75 core problem.
2. **A fully crafted problem statement in your own words** — a real paragraph, so he can attempt it
   on the page without leaving. Do not just link out.
3. **Example 1 / Example 2** (and a 3rd when it exercises a distinct failure mode), each with input,
   output, and a short *why*. Then a **Constraints:** line.
4. `<p><a href="https://leetcode.com/problems/SLUG/" target="_blank" rel="noopener">Solve on LeetCode ↗</a></p>`
   — the slug MUST be the real LeetCode slug. Do not invent one.
5. **`<strong>Thinking process.</strong>`** — a paragraph that derives the solution from the brute
   force. State the brute force, say why it's too slow, then the insight that collapses it. This is
   the most valuable part of the page. It doubles as the hint the reader reveals nothing to see.
6. `<details class="qa"><summary>Solution (JS) — O(?) time · O(?) space</summary><div class="answer">`
   containing:
   - a `<pre><code>` JS solution, **heavily commented**, in LeetCode's `var fn = function(...) {}`
     or `class` form so it pastes straight into the site.
   - a `<strong>Trace:</strong>` walking Example 1 through the code concretely with real values.
   - a `<strong>Complexity:</strong>` paragraph justifying both time and space.
   - a `<strong>Follow-ups you should expect:</strong>` `<ul>` — the real ones interviewers ask next.

## Callouts — use them, don't overuse them
- `<div class="pitfall">` the specific wrong turn candidates take here. Be concrete.
- `<div class="note">` a JS-specific gotcha or a useful aside.
- `<div class="senior">` the thing a 7-YOE candidate says that a 2-YOE candidate doesn't.
Aim for roughly one callout per problem, never two in a row.

## Code rules
- **JavaScript only.** Idiomatic modern JS.
- Syntax-highlight by hand with spans — the stylesheet defines them:
  `<span class="kw">` keywords · `<span class="str">` strings · `<span class="com">` comments ·
  `<span class="num">` numbers · `<span class="typ">` types.
- HTML-escape inside `<pre>`: `&lt;` `&gt;` `&amp;`. A raw `<` or `&&` in code will break the page.
  This is the #1 way these files get corrupted — check every comparison operator you write.
- Comments must explain *why*, not restate the line.

## Non-negotiables
- Cover every problem named on this tutorial's index.html card. Nothing dropped, nothing added.
- The page must be **complete and closed** — `</main></body></html>`. Never trail off mid-section.
  Do not summarize or shorten late sections because you are running long; the last problem gets the
  same depth as the first.
- Self-contained: no CDN, no JS, no external assets. Only `styles.css`, which already exists — do
  not modify or re-create it.
