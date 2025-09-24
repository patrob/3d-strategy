3D Strategy Phases
===================

Concise, repeatable flow for moving an idea from fuzzy problem space to operating, measured reality. The three core phases — Discovery, Design, Delivery — keep discovery, design, and delivery cleanly separated while maintaining tight feedback loops.

Quick Links
-----------
| Phase | Purpose (1‑liner) | Primary Outputs |
|-------|-------------------|------------------|
| [Discovery](Discovery.md) | Build context & insight | Problem framing, users, constraints, option set |
| [Design](Design.md) | Decide what to do & how | Chosen solution, scope, sequencing, resourcing, success metrics |
| [Delivery](Delivery.md) | Ship & learn | Working increments, telemetry, learnings, deltas |

Why This Exists
---------------
Reduce churn, hidden assumptions, and premature solutioning. Each phase has a clearly defined exit state; you should not “half enter” the next phase. Lightweight by default; deepen only where risk, ambiguity, or impact justify it.

Phase Overviews
---------------
### 1. Discovery
Goal: Convert uncertainty into a structured understanding of problem, users, constraints, and viable solution approaches.
You leave Discovery with: a crisply stated problem, success definition, option tradeoffs, and a recommended direction (NOT a detailed build plan yet).

### 2. Design
Goal: Turn the selected direction into an executable path. Slice scope, define architecture/approach, surface risks, establish metrics & checkpoints.
You leave Design with: bounded scope, milestone map, resource assumptions, risk register, and measurable success criteria.

### 3. Delivery
Goal: Deliver smallest meaningful slices to production (or realistic environments) fast, measure, adapt.
You leave Delivery when: agreed scope is shipped OR a pivot/kill decision is justified by data.

Flow (Idealized)
----------------
```
	Ambiguity
		↓
  [Discovery]
		↓ (problem framed, option chosen)
	 [Design]
		↓ (scope + path locked)
 [Delivery] ↺ (iterate with data)
		↓
	Outcome / Next Bet
```

Gating Checklist
----------------
Use these to confirm you are *truly* done with a phase:

Discovery → Design:
- Problem statement: specific, user-centered, testable.
- Success definition: leading + lagging metrics, initial targets or directional hypotheses.
- Option set documented with tradeoffs (including “do nothing / defer”).
- Recommended direction + rationale.
- Critical unknowns & assumptions explicitly listed.

Design → Delivery:
- Scope sliced into milestones / increments (each demonstrable).
- Architecture / approach sketched (just enough to reduce rework risk).
- Resource & dependency map (people, data, tooling, external).
- Risks ranked w/ mitigations or acceptance rationale.
- Metrics instrumentation approach (where + how captured) agreed.
- Definition of Done (per increment + overall) captured.

Delivery → Close / Next:
- Agreed scope delivered OR recalibrated with stakeholder sign‑off.
- Metrics collected + compared to targets / hypotheses.
- Post-impact summary: what worked, what missed, key learnings.
- Backlog triage: follow-on items categorized (Now / Next / Later / Drop).
- Documentation & handoff (if ongoing operations needed) complete.

Core Artifacts by Phase
-----------------------
- Discovery: Problem Brief, Option Matrix, Stakeholder / User Insights, Assumptions Log.
- Design: Execution Design (milestones), Architecture/Design Sketch, Risk Register, Measurement Design.
- Delivery: Increment Changelog, Metrics Dashboard / Snapshots, Decision Log, Post-Deliveryation Review.

Working Cadences
----------------
- Daily (Delivery): progress, blockers, metric anomalies.
- Weekly (Discovery/Design): alignment sync / decision checkpoint (end early if not needed).
- Phase Transition Review: 30–45 min focused acceptance of gating checklist.

Roles (Flexible Hats)
---------------------
- Driver: maintains momentum & artifact integrity.
- Domain / Tech Lead(s): feasibility calls, architecture input.
- Product / Customer Voice: validates problem framing & value.
- Metrics Steward: ensures measurability is real, not aspirational.

Adapting the Depth
------------------
| Context | Discovery Depth | Design Depth | Delivery Mode |
|---------|----------------|-----------|-----------------|
| High risk / High impact | Deep | Deep | Tight iteration + telemetry |
| Low risk / Routine | Lean (fast capture) | Minimal (just milestones) | Standard sprint rhythm |
| Exploratory spike | Lightweight framing | Possibly skipped | Prototype & evaluate |

How to Use This Folder
----------------------
1. Start a new effort by creating a subfolder (e.g. `initiative-X/`) with `Discovery.md`, `Design.md`, `Delivery.md` templates copied or linked.
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
- Skipping Discovery because “solution is obvious” (later rework proves it wasn’t).
- Over-specifying Design (faux certainty) in high-unknown spaces.
- Giant Delivery batch with no intermediate validation.
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
Fast Start TL;DR: Frame the problem (Discovery) → Decide & slice (Design) → Ship small, measure, learn (Delivery). Don’t promote a phase until its exit checklist is undeniably met.

