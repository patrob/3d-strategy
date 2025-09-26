# FACTS Scale (Design Phase Validation)

The FACTS Scale validates Design phase outputs by measuring five critical dimensions of technical implementation plan quality. Task breakdowns must achieve a mean score of 3.00 or higher across all dimensions to proceed to the Delivery phase.

## Validation Rules

### Pass Criteria
- **Mean Score**: Average of all five dimensions must be >= 3.00
- **Precision**: Calculate mean to exactly 2 decimal places (no additional rounding)
- **Threshold**: Pass required for phase completion

### Failure Handling
- **On Failure**: Restart full Design workflow (refine → validate → FACTS)
- **Scoring Actor**: Design Agent (automated) with optional human override
- **Mean Calculation**: Arithmetic average of F, A, C, T, S dimensions

## Scoring Dimensions

### Feasibility — "Can this be implemented with available resources?"

**0 — Impossible**
- Task requires non-existent technology or violates fundamental constraints

**1 — Expert Only**
- Requires deep domain expertise, multiple senior developers, or extensive research

**2 — Advanced**
- Needs experienced developer with specific framework knowledge and significant investigation

**3 — Intermediate**
- Junior developer can complete with mentoring and some research/documentation review

**4 — Straightforward**
- Junior developer can complete independently with standard documentation

**5 — Trivial**
- Can be completed by copy-paste, configuration change, or single API call

### Atomicity — "Is this task focused on a single responsibility?"

**0 — Massive**
- Task spans multiple systems, requires weeks of work, affects dozens of files

**1 — Large**
- Single feature but touches many components, requires multiple PRs to review safely

**2 — Medium**
- Clear feature boundary but involves several related changes across multiple files

**3 — Focused**
- Single responsibility with minimal cross-cutting concerns, 2-5 file changes

**4 — Targeted**
- One clear objective, 1-3 file changes, single aspect of functionality

**5 — Atomic**
- Indivisible unit of work, single file change, one logical modification

### Clarity — "Is the execution order and dependencies clear?"

**0 — Chaotic**
- No clear execution order, circular dependencies, conflicting requirements

**1 — Ambiguous**
- Dependencies exist but are unclear, multiple valid interpretation paths

**2 — Fuzzy**
- General order apparent but specific sequencing decisions left to implementer

**3 — Structured**
- Dependencies identified, execution order determinable with minor investigation

**4 — Ordered**
- Clear prerequisite chain, unambiguous next step at each stage

**5 — Sequential**
- Perfect linear dependency chain, each task enables exactly the next one

### Testability — "Can completion be verified?"

**0 — Untestable**
- No way to verify completion, purely subjective outcomes

**1 — Manual Only**
- Requires extensive manual testing, no automated verification possible

**2 — Observable**
- Completion visible through logs/UI but requires complex setup to verify

**3 — Demonstrable**
- Clear pass/fail criteria, can be tested but requires some manual steps

**4 — Verifiable**
- Automated tests can validate completion, clear success metrics

**5 — Provable**
- Unit tests, integration tests, or simple commands definitively prove completion

### Size — "Is the task appropriately scoped?"

**0 — Enormous**
- Multiple systems, cross-team coordination, requires comprehensive project planning

**1 — Large**
- Single feature spanning many files, multiple complex interconnected changes

**2 — Medium**
- Feature with several related changes, moderate cross-cutting concerns

**3 — Standard**
- Focused task with clear boundaries, typical development work

**4 — Small**
- Straightforward implementation, minimal scope, well-defined change

**5 — Tiny**
- Atomic unit: single file edit, configuration change, or simple command

## Scoring Format

```
F: [score]  A: [score]  C: [score]  T: [score]  S: [score]  Mean: [X.XX]  --> [PASS/FAIL]
```

## Examples

**Pass Examples:**
```
F: 4  A: 3  C: 3  T: 4  S: 3  Mean: 3.40  --> PASS
F: 3  A: 3  C: 3  T: 3  S: 3  Mean: 3.00  --> PASS
```

**Fail Examples:**
```
F: 3  A: 2  C: 3  T: 3  S: 3  Mean: 2.80  --> FAIL (Mean < 3.00)  (Restart)
F: 1  A: 4  C: 4  T: 4  S: 4  Mean: 3.40  --> FAIL (F < 3 indicates infeasible tasks)
```

## Best Practices

### Task Design Guidelines
- **Single Responsibility**: Each task should accomplish exactly one objective
- **Clear Boundaries**: Task completion should be unambiguously verifiable
- **Appropriate Sizing**: Balance granularity with atomic simplicity (single command calls, file edits, etc.)
- **Dependency Clarity**: Make prerequisites explicit and non-circular
- **Context Sufficiency**: Include enough information for independent execution

### Common Anti-Patterns
- Tasks requiring multiple unrelated changes
- Ambiguous completion criteria
- Circular or unclear dependencies
- Extreme size variations within phases
- Requirements for specialized knowledge not documented