RPI Strategy Phases
===================

Concise, repeatable flow for moving an idea from fuzzy problem space to operating, measured reality. The three core phases — Research, Plan, Implement — keep discovery, design, and delivery cleanly separated while maintaining tight feedback loops.

Quick Links
-----------
| Phase | Purpose (1‑liner) | Primary Outputs |
|-------|-------------------|------------------|
| [Research](Research.md) | Build context & insight | Problem framing, users, constraints, option set |
| [Plan](Plan.md) | Decide what to do & how | Chosen solution, scope, sequencing, resourcing, success metrics |
| [Implement](Implement.md) | Ship & learn | Working increments, telemetry, learnings, deltas |

Why This Exists
---------------
Reduce churn, hidden assumptions, and premature solutioning. Each phase has a clearly defined exit state; you should not “half enter” the next phase. Lightweight by default; deepen only where risk, ambiguity, or impact justify it.

Phase Overviews
---------------
### 1. Research
Goal: Convert uncertainty into a structured understanding of problem, users, constraints, and viable solution approaches.
You leave Research with: a crisply stated problem, success definition, option tradeoffs, and a recommended direction (NOT a detailed build plan yet).

### 2. Plan
Goal: Turn the selected direction into an executable path. Slice scope, define architecture/approach, surface risks, establish metrics & checkpoints.
You leave Plan with: bounded scope, milestone map, resource assumptions, risk register, and measurable success criteria.

### 3. Implement
Goal: Deliver smallest meaningful slices to production (or realistic environments) fast, measure, adapt.
You leave Implement when: agreed scope is shipped OR a pivot/kill decision is justified by data.

Flow (Idealized)
----------------
```
	Ambiguity
		↓
  [Research]
		↓ (problem framed, option chosen)
	 [Plan]
		↓ (scope + path locked)
 [Implement] ↺ (iterate with data)
		↓
	Outcome / Next Bet
```

Gating Checklist
----------------
Use these to confirm you are *truly* done with a phase:

Research → Plan:
- Problem statement: specific, user-centered, testable.
- Success definition: leading + lagging metrics, initial targets or directional hypotheses.
- Option set documented with tradeoffs (including “do nothing / defer”).
- Recommended direction + rationale.
- Critical unknowns & assumptions explicitly listed.

Plan → Implement:
- Scope sliced into milestones / increments (each demonstrable).
- Architecture / approach sketched (just enough to reduce rework risk).
- Resource & dependency map (people, data, tooling, external).
- Risks ranked w/ mitigations or acceptance rationale.
- Metrics instrumentation approach (where + how captured) agreed.
- Definition of Done (per increment + overall) captured.

Implement → Close / Next:
- Agreed scope delivered OR recalibrated with stakeholder sign‑off.
- Metrics collected + compared to targets / hypotheses.
- Post-impact summary: what worked, what missed, key learnings.
- Backlog triage: follow-on items categorized (Now / Next / Later / Drop).
- Documentation & handoff (if ongoing operations needed) complete.

Core Artifacts by Phase
-----------------------
- Research: Problem Brief, Option Matrix, Stakeholder / User Insights, Assumptions Log.
- Plan: Execution Plan (milestones), Architecture/Design Sketch, Risk Register, Measurement Plan.
- Implement: Increment Changelog, Metrics Dashboard / Snapshots, Decision Log, Post-Implementation Review.

Working Cadences
----------------
- Daily (Implement): progress, blockers, metric anomalies.
- Weekly (Research/Plan): alignment sync / decision checkpoint (end early if not needed).
- Phase Transition Review: 30–45 min focused acceptance of gating checklist.

Roles (Flexible Hats)
---------------------
- Driver: maintains momentum & artifact integrity.
- Domain / Tech Lead(s): feasibility calls, architecture input.
- Product / Customer Voice: validates problem framing & value.
- Metrics Steward: ensures measurability is real, not aspirational.

Adapting the Depth
------------------
| Context | Research Depth | Plan Depth | Implement Mode |
|---------|----------------|-----------|-----------------|
| High risk / High impact | Deep | Deep | Tight iteration + telemetry |
| Low risk / Routine | Lean (fast capture) | Minimal (just milestones) | Standard sprint rhythm |
| Exploratory spike | Lightweight framing | Possibly skipped | Prototype & evaluate |

How to Use This Folder
----------------------
1. Start a new effort by creating a subfolder (e.g. `initiative-X/`) with `Research.md`, `Plan.md`, `Implement.md` templates copied or linked.
2. Fill only what adds clarity; avoid performative docs.
3. Keep artifacts in-source (versioned) for transparency.
4. Link decisions (PRs, issues) directly inside phase docs.

Suggested Template Snippet (Problem Statement)
---------------------------------------------
Problem:
- Who is impacted?
- What friction or gap exists?
- Why now (trigger / urgency)?
Evidence:
- Qualitative (quotes / observations)
- Quantitative (metrics / trends)
Success (initial hypothesis):
- Leading metric(s):
- Lagging outcome metric(s):

Decision Logging
----------------
Capture meaningful direction changes as short, immutable entries:
`YYYY-MM-DD | Decision | Context | Alternatives | Rationale | Owner`

Anti-Patterns to Avoid
----------------------
- Skipping Research because “solution is obvious” (later rework proves it wasn’t).
- Over-specifying Plan (faux certainty) in high-unknown spaces.
- Giant Implement batch with no intermediate validation.
- Metrics added after shipping (missed baselines).

Related Docs
------------
See higher-level strategy material in `../far-scale/` for scaling principles and governance concepts that complement these phases.

License
-------
This content inherits the repository license (see root `LICENSE`).

Feedback / Improvements
-----------------------
Open an issue or PR: propose concise changes with rationale; prefer examples over abstract suggestions.

---
Fast Start TL;DR: Frame the problem (Research) → Decide & slice (Plan) → Ship small, measure, learn (Implement). Don’t promote a phase until its exit checklist is undeniably met.

