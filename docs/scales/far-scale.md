# FAR Scale (Discovery Phase Validation)

The FAR Scale validates Discovery phase outputs by measuring three critical dimensions of code-focused investigation. Discovery findings must achieve specific pass criteria across all dimensions to proceed to the Design phase.

## Validation Rules

### Pass Criteria
- **Factual (F)**: >= 4 (minimum threshold for evidence quality)
- **Actionable (A)**: >= 3 (minimum threshold for implementation readiness)
- **Relevant (R)**: >= 3 (minimum threshold for problem alignment)
- **Mean Score**: >= 4.00 (overall quality threshold)
- **Precision**: All scores calculated to 2 decimal places (no additional rounding)

### Failure Handling
- **On Failure**: Restart full Discovery workflow (clarify → analyze → validate → FAR)
- **Scoring Actor**: Discovery Agent (automated) with optional human override
- **Mean Calculation**: Arithmetic average of F, A, R dimensions

## Scoring Dimensions

### Factual — "Is this evidenced in the code/system?"

**0 — Fabricated**
- Contradicts code/architecture; no artifacts; synthetic/edited logs

**1 — Rumor**
- Hearsay in chat/issue; no repro, logs, or code references

**2 — Single-source, weak provenance**
- One screenshot/log snippet or lone comment; indirect evidence; no deterministic repro

**3 — Provisionally credible**
- Partial/occasional repro; stack trace/module matches; one failing test locally or clear call path hypothesis

**4 — Corroborated**
- Deterministic repro; multiple environments/users; call graph/commit history aligns; added failing test or trace confirms

**5 — Strongly verified**
- Minimal repro + automated failing test; root-cause lines identified; bisected to commit/flag/config; owner review concurs

**Scoring cues:**
- Prefer source/tests/CI and traces over docs or anecdotes
- Deterministic repro + code reference is >= 4
- Bisect + failing test typically = 5

### Actionable — "Can I move this forward now?"

**0 — No action possible**
- No repro, no hypothesis, no access

**1 — Vague/long-term only**
- Needs large refactor/org changes; unclear ownership or env access

**2 — Directional, heavy lift**
- Hypothesis exists; requires env bootstrap, data seeding, or harness work before testing

**3 — Concrete next step exists**
- Specific file/function to probe; add logs/guards; author a failing test or reproduce locally this week

**4 — Clear, low-friction plan**
- Stepwise fix plan; owner known; small PR/config change; risk noted; validation path defined

**5 — Immediate, high-leverage, within control**
- One-liner or flag flip; failing test guides fix; can open PR < 60 min; success measurable via test/metric/CI

**Scoring cues:**
- If you can start today with known steps/tools, it's >= 3
- Small diff + clear validation pushes to 4-5

### Relevant — "Does it matter to this ticket/story now?"

**0 — Off-topic**
- Unrelated subsystem or external product; no impact on acceptance criteria

**1 — Tangential**
- Neighboring area; theoretical risk, low priority

**2 — Adjacent/general interest**
- Related subsystem behavior but not blocking success criteria

**3 — On-theme**
- Within the component/surface; affects acceptance criteria or tests, but not blocking today

**4 — Core + timely**
- Blocks ticket or degrades SLA/CI reliability; within team ownership; aligned to current sprint

**5 — Bullseye for now**
- Directly unblocks critical path or prod incident; customer impact measurable; you have unique context/assets

**Scoring cues:**
- If it blocks the story/bug now, score >= 4
- Customer/SLA impact and clear ownership push to 5

## Quick Examples

**Factual 5**: git bisect isolates commit; failing unit test reproduces; stack trace matches call path

**Actionable 5**: Add null check + test; PR in < 30 min; CI turns green

**Relevant 5**: Fix required to meet current story's acceptance criteria

## Scoring Format

```
F: [score]  A: [score]  R: [score]  Mean: [X.XX]  --> [PASS/FAIL]
```

**Pass Example:**
```
F: 4  A: 4  R: 4  Mean: 4.00  --> PASS
```

**Fail Example:**
```
F: 4  A: 3  R: 4  Mean: 3.67  --> FAIL (Mean < 4.00)  (Restart)
```