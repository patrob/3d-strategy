RPI Strategy Phases
===================

Concise, repeatable flow for moving an idea from fuzzy problem space to operating, measured reality. The three core phases — Research, Plan, Implement — keep research, planning, and implementation cleanly separated while maintaining tight feedback loops.

Quick Links
-----------
| Phase | Purpose (1‑liner) | Primary Outputs |
|-------|-------------------|------------------|
| [Research](Discovery.md) | Build context & insight | Problem framing, users, constraints, option set |
| [Plan](Design.md) | Decide what to do & how | Chosen solution, scope, sequencing, resourcing, success metrics |
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

## Research → Plan Success Criteria

**Required Artifacts:**
- Problem statement (50-200 words) validated against [FAR scale](../scales/far-scale.md) (Mean ≥4.00)
- 3-5 user stories with specific acceptance criteria
- Technical constraints documented (performance, security, integration requirements)
- Resource requirements estimated (time, people, external dependencies)
- Option set with explicit tradeoffs (including "do nothing" analysis)

**Validation Checkpoints:**
- [ ] Problem statement reviewed by 2+ team members outside core team
- [ ] User stories directly map to measurable business value
- [ ] Technical feasibility confirmed by technical lead with implementation experience
- [ ] FAR scale scoring: Factual≥4, Actionable≥3, Relevant≥3 (out of 5), Mean≥4.00
- [ ] Critical unknowns identified with investigation plans

**Failure Triggers:**
- FAR scale scores <4.0 after 2 revision attempts
- Unable to define measurable acceptance criteria for user stories
- Resource requirements exceed project constraints by >50%
- Technical constraints create circular dependencies

## Plan → Implement Success Criteria

**Required Artifacts:**
- Task breakdown with all individual tasks as atomic units (single command calls, file edits, etc.)
- Dependency graph showing task relationships and critical path
- Interface definitions for all external integrations
- Testing strategy with specific coverage targets (>80% for critical paths)
- Risk register with mitigation plans for high-probability impacts

**Validation Checkpoints:**
- [ ] All tasks have clear, testable definition of done
- [ ] Critical path identified and timeline validated by implementer
- [ ] Risk mitigation plans assigned to specific owners with dates
- [ ] [FACTS scale](../scales/facts-scale.md) scoring: Mean≥3.00 across all dimensions (out of 5)
- [ ] Architecture decisions documented with rationale

**Failure Triggers:**
- Any individual task too complex to be atomic (return to Research for problem decomposition)
- FACTS scale scores <3.0 after 2 revision attempts
- Circular dependencies discovered in task graph
- Critical path >150% of original timeline estimate

## Implement → Close/Next Success Criteria

**Required Artifacts:**
- All agreed scope delivered OR formal scope change approved by stakeholders
- Metrics dashboard with baseline vs. actual performance data
- Post-implementation review documenting what worked, what missed, key learnings
- Backlog triage with items categorized (Now/Next/Later/Drop) and ownership
- Production handoff documentation (if ongoing operations required)

**Validation Checkpoints:**
- [ ] Deliverables pass acceptance criteria from Plan phase
- [ ] Metrics targets achieved OR variance explained with stakeholder agreement
- [ ] Performance meets technical constraints defined in Research
- [ ] Security and integration requirements validated in production environment
- [ ] Knowledge transfer completed to operations/maintenance team

**Failure Triggers:**
- 3+ consecutive implementation attempts fail validation criteria
- Critical path blocked >2 days without resolution plan
- Security or data integrity issues discovered in production
- Metrics show >25% degradation from baseline without mitigation plan

Core Artifacts by Phase
-----------------------
- Research: Problem Brief, Option Matrix, Stakeholder / User Insights, Assumptions Log.
- Plan: Execution Plan (milestones), Architecture/Design Sketch, Risk Register, Measurement Design.
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

Failure Handling Framework
---------------------------
Each phase includes comprehensive failure handling with specific criteria, escalation paths, and recovery procedures:

### Failure Classification System
**Minor Failures**: Single iteration fixes, local guidance needed
- Research: FAR scores 3.5-3.9
- Plan: FACTS scores 2.8-2.9
- Implement: Individual task quality gate failures

**Major Failures**: Phase restart required, stakeholder consultation
- Research: FAR scores 2.0-3.4, missing critical context
- Plan: FACTS scores 2.0-2.7, task breakdown insufficient
- Implement: 2+ consecutive task failures, critical path blocked with no clear resolution

**Critical Failures**: Leadership escalation, project viability assessment
- Research: FAR scores <2.0, fundamental problem misunderstanding
- Plan: FACTS scores <2.0, circular dependencies detected
- Implement: 3+ consecutive failures, security/integrity issues, >2 day blocks

### Escalation Timeline
| Failure Level | Response Time | Action Required | Decision Authority |
|---------------|---------------|-----------------|-------------------|
| Minor | Same session | Local revision/consultation | Team lead |
| Major | Same day | Phase restart with enhanced context | Technical lead |
| Critical | Immediate | Leadership escalation, project pause | Engineering manager |

### Recovery Paths
**Phase Transitions on Failure**:
- Research ← Plan: When planning reveals insufficient problem understanding
- Research ← Implement: When implementation reveals fundamental scope issues
- Plan ← Implement: When task breakdown proves inadequate for implementation

**Preservation Rules**:
- Always preserve validated artifacts from higher phases
- Pass context about specific failures to inform restart
- Document lessons learned for process improvement

### Postmortem Requirements
Critical failures generate standardized postmortem documents:
- **research-postmortem.md**: Problem understanding gaps, context needs
- **plan-postmortem.md**: Task breakdown analysis, architectural concerns
- **implement-postmortem.md**: Implementation blockers, technical constraints

This framework provides complete failure handling guidance for all phases. Individual phase documents reference this centralized framework for consistent application.

Anti-Patterns to Avoid
----------------------
- Skipping Research because "solution is obvious" (later rework proves it wasn't).
- Over-specifying Plan (faux certainty) in high-unknown spaces.
- Giant Implement batch with no intermediate validation.
- Metrics added after shipping (missed baselines).
- Proceeding with failed validation scores to "make progress" (compounds problems).
- Treating all failures the same (minor issues get over-escalated, critical issues get under-addressed).

Related Docs
------------
See validation frameworks that support phase quality gates:
- Code validation criteria: [FAR Scale](../scales/far-scale.md)
- Design validation guidelines: [FACTS Scale](../scales/facts-scale.md)

These scales provide objective scoring criteria for phase transition decisions.

License
-------
This content inherits the repository license (see root `LICENSE`).

Feedback / Improvements
-----------------------
Open an issue or PR: propose concise changes with rationale; prefer examples over abstract suggestions.

---
Fast Start TL;DR: Frame the problem (Research) → Decide & slice (Plan) → Ship small, measure, learn (Implement). Don’t promote a phase until its exit checklist is undeniably met.

