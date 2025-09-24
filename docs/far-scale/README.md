## Using the FAR Scale to Improve GenAI (and human) Results

The FAR Scale is a lightweight rubric to make prompts and outputs more reliable and useful. It scores three dimensions from 0–5:

- Factual — “Is it true/evidenced?”
- Actionable — “Can I move this forward now?”
- Relevant — “Does it matter to the goal right now?”

Two variants are included in this folder:

- Generic FAR Scale for research, content, and strategy: [`FAR-Scale-Generic.md`](./FAR-Scale-Generic.md)
- Codebase Research FAR Scale tailored to software work: [`FAR-Scale-for-Code.md`](./FAR-Scale-for-Code.md)

Use the Generic scale when you’re asking for facts, analysis, or content. Use the Code scale when you’re debugging, changing code, or validating engineering claims.


## Quickstart

1) Pick the right scale (Generic vs Code).  
2) Paste the “What good looks like” summary (or just link to the file) into your prompt.  
3) Ask the model to self‑score F/A/R and enforce the filter threshold before finalizing.  
4) Require evidence for “Factual,” a concrete next step for “Actionable,” and a clear tie‑back to your objective for “Relevant.”  
5) Iterate until thresholds are met, then proceed.

### Filter threshold (from the FAR Scale files)

- Factual must always be a 4 or higher to move forward.  
- Overall FAR score must be a 4 or higher to move forward.  

Note: Teams often treat “overall” as either the minimum of the three scores or an average. Whatever you choose, still enforce Factual ≥4 as an absolute gate. If you use average, avoid masking weak dimensions (e.g., consider adding a floor like no dimension <3).


## Prompt templates

### A. Generic FAR self‑check (research/content)

```
You are helping with [goal/outcome]. Use the FAR Scale (Factual, Actionable, Relevant) with 0–5 scoring described here: https://…/docs/far-scale/FAR-Scale-Generic.md (or paste rubric).

Task:
- [Describe the question/request]

Requirements:
- Cite primary sources for key claims. Prefer docs, filings, datasets over blogs.
- Propose at least one concrete next step I can do this week.
- Tie recommendations to [current objective/milestone].

Deliver:
1) Draft answer
2) FAR scores with one‑line justification per dimension
3) Evidence list (links/quotes)
4) Next steps (owners, effort, expected result)
5) Revisions needed to satisfy: Factual ≥4 AND Overall FAR ≥4 (optionally target 4/4/4); then provide the improved answer
```

### B. Codebase FAR self‑check (debug/fix/PR)

```
You are working in this repo: [name/link]. Use the FAR Scale for Codebase Research: https://…/docs/far-scale/FAR-Scale-for-Code.md (or paste rubric).

Task:
- [Bug/feature request]

Constraints:
- Prefer deterministic repro and a failing automated test.
- Reference specific files, functions, and line ranges when making claims.
- Don’t change public APIs unless justified; note risk and validation plan.

Deliver:
1) Repro steps (minimal)
2) Factual evidence: stack traces, call graphs, code lines, commit history
3) Actionable plan: failing test first, then fix, then validation
4) Relevant: tie back to acceptance criteria/SLA/sprint goal
5) FAR scores + what it would take to satisfy: Factual ≥4 AND Overall FAR ≥4 before merge (optionally target 4/4/4)
```

### C. Reviewer prompt (useful for PRs or content drafts)

```
Act as a reviewer using the appropriate FAR Scale (Generic or Code). Provide:
- FAR scores with 1–2 line rationale each
- Missing evidence or weak links
- Specific edits or tests needed to meet: Factual ≥4 AND Overall FAR ≥4 (and ideally 4/4/4)
- Risk notes and a minimal validation path
```


## Thresholds and usage patterns

- Exploration/brainstorming: Sub‑4 scores are acceptable for ideation, but before you move forward (execute/publish/merge), apply the filter (Factual ≥4 and Overall ≥4).
- Publishing or external claims: Apply the filter; aim for ≥4/4/4 with primary sources.
- Shipping code/PR merge: Apply the filter; in practice target Factual ≥4 (deterministic repro or primary code evidence) and a clear validation plan. If your team uses average for “overall,” avoid proceeding with any dimension <3.
- Hotfix/incident: Apply the filter; emphasize Actionable validation and rollback.

Tip: Make the threshold explicit in your prompt: “Do not finalize or proceed until Factual ≥4 AND Overall FAR ≥4; if you cannot reach it, list blockers and the smallest next experiment.”


## How FAR improves results

- Reduces hallucinations: Factual requires evidence and direct code/doc references.
- Drives momentum: Actionable demands clear next steps and small, testable changes.
- Aligns to goals: Relevant prevents great work on the wrong problem.
- Encourages test‑first fixes: The Code scale treats failing tests and bisection as first‑class evidence.
- Shortens the loop: High scores map to measurable, verifiable outcomes.


## Example workflows

### 1) Research task (Generic)

1. Ask for a summary and require citations.  
2. Model self‑scores; it flags that a key claim lacks a primary source (Factual=2).  
3. It proposes contacting the author or checking a dataset (Actionable=3).  
4. You raise the bar to ≥4, it finds a primary source and rewrites the section, adds a 1‑week next step with metric.  
5. Final answer reaches 4/4/4 with links and a clear plan.

### 2) Bug fix (Code)

1. Ask the model to create a minimal repro and an automated failing test.  
2. It ties an exception to a specific function and commit (Factual=4).  
3. It provides a one‑liner fix and a validation checklist (Actionable=4).  
4. It explains why this matters for the current ticket (Relevant=4).  
5. You review, run tests, and merge.


## Team adoption ideas

- Add a “FAR line” to PR templates: “F/A/R = x/x/x; evidence: [links]; validation: [steps].”
- Require FAR in incident timelines: what raised each score and when.
- In planning, ask for FAR on proposals; only schedule items ≥3/4/4 or with a short path to get there.
- For content, keep a sources appendix and tag each claim with F scores.


## Tips and pitfalls

Do:
- Ask for quotes/links to primary docs or code lines.
- Insist on a concrete next step with owner and effort.
- Tie recommendations to a live objective, ticket, or SLA.

Avoid:
- “Score inflation” without adding evidence or tests.
- Perfection paralysis; for exploration, 3/3/3 is often enough.
- Vague “future work” without a first, doable step.


## Quick reference (abridged)

- Factual ≥4: Multiple sources or deterministic repro; primary artifacts or code references present.  
- Actionable ≥4: Clear, low‑friction plan; validation path and success metric defined.  
- Relevant ≥4: Directly supports current objective; timely and within team scope.

Filter threshold to move forward:

- Factual ≥4 AND Overall FAR ≥4

For full detail, see the scale definitions:

- Generic: [`FAR-Scale-Generic.md`](./FAR-Scale-Generic.md)  
- Code: [`FAR-Scale-for-Code.md`](./FAR-Scale-for-Code.md)


---

If you want, we can tailor these templates to your repo/tooling (e.g., add file paths, test runners, and CI gates) so the “Actionable” steps map 1:1 to your workflows.

