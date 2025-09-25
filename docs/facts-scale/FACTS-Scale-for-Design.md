# FACTS Scale for Technical Implementation Plans

## Overview
The FACTS Scale validates technical implementation plans by measuring five critical dimensions of task breakdown quality. Plans must achieve a mean score of 3.00 or higher across all dimensions to proceed to the Delivery phase.

## Scoring Dimensions

### Feasibility
0: **Impossible** - Task requires non-existent technology or violates fundamental constraints
1: **Expert Only** - Requires deep domain expertise, multiple senior developers, or extensive research
2: **Advanced** - Needs experienced developer with specific framework knowledge and significant investigation
3: **Intermediate** - Junior developer can complete with mentoring and some research/documentation review
4: **Straightforward** - Junior developer can complete independently with standard documentation
5: **Trivial** - Can be completed by copy-paste, configuration change, or single API call

### Atomicity
0: **Massive** - Task spans multiple systems, requires weeks of work, affects dozens of files
1: **Large** - Single feature but touches many components, requires multiple PRs to review safely
2: **Medium** - Clear feature boundary but involves several related changes across multiple files
3: **Focused** - Single responsibility with minimal cross-cutting concerns, 2-5 file changes
4: **Targeted** - One clear objective, 1-3 file changes, single aspect of functionality
5: **Atomic** - Indivisible unit of work, single file change, one logical modification

### Clarity
0: **Chaotic** - No clear execution order, circular dependencies, conflicting requirements
1: **Ambiguous** - Dependencies exist but are unclear, multiple valid interpretation paths
2: **Fuzzy** - General order apparent but specific sequencing decisions left to implementer
3: **Structured** - Dependencies identified, execution order determinable with minor investigation
4: **Ordered** - Clear prerequisite chain, unambiguous next step at each stage
5: **Sequential** - Perfect linear dependency chain, each task enables exactly the next one

### Testability
0: **Untestable** - No way to verify completion, purely subjective outcomes
1: **Manual Only** - Requires extensive manual testing, no automated verification possible
2: **Observable** - Completion visible through logs/UI but requires complex setup to verify
3: **Demonstrable** - Clear pass/fail criteria, can be tested but requires some manual steps
4: **Verifiable** - Automated tests can validate completion, clear success metrics
5: **Provable** - Unit tests, integration tests, or simple commands definitively prove completion

### Size
0: **Enormous** - 40+ hours, multiple sprints, cross-team coordination required
1: **Large** - 2-3 days of focused work, significant complexity or scope
2: **Medium** - 1-2 days, moderate complexity, standard development task
3: **Standard** - 4-8 hours, typical feature development or bug fix
4: **Small** - 1-4 hours, straightforward implementation or minor change
5: **Tiny** - < 1 hour, configuration change, simple addition, or obvious fix

## Validation Rules

### Pass Criteria
- **Mean Score**: Average of all five dimensions must be ≥ 3.00
- **Precision**: Calculate mean to exactly 2 decimal places
- **No Rounding**: Use arithmetic mean without additional rounding

### Failure Response
- Any plan scoring below 3.00 mean must be refined
- Return to task breakdown and dependency analysis
- Retain valid artifacts unless invalidated by changes
- Restart validation process with updated plan

### Scoring Format
```
F: [0-5]  A: [0-5]  C: [0-5]  T: [0-5]  S: [0-5]  Mean: [X.XX]  --> [PASS/FAIL]
```

## Examples

### Passing Score Examples
```
F: 4  A: 3  C: 3  T: 4  S: 3  Mean: 3.40  --> PASS
F: 3  A: 3  C: 3  T: 3  S: 3  Mean: 3.00  --> PASS
F: 5  A: 2  C: 3  T: 4  S: 1  Mean: 3.00  --> PASS
```

### Failing Score Examples
```
F: 3  A: 2  C: 3  T: 3  S: 3  Mean: 2.80  --> FAIL (Mean < 3.00)
F: 1  A: 4  C: 4  T: 4  S: 4  Mean: 3.40  --> FAIL (F < 3 indicates infeasible tasks)
F: 4  A: 1  C: 3  T: 3  S: 4  Mean: 3.00  --> FAIL (A < 3 indicates non-atomic tasks)
```

## Best Practices

### Task Design Guidelines
- **Single Responsibility**: Each task should accomplish exactly one objective
- **Clear Boundaries**: Task completion should be unambiguously verifiable
- **Appropriate Sizing**: Balance granularity with practical execution time
- **Dependency Clarity**: Make prerequisites explicit and non-circular
- **Context Sufficiency**: Include enough information for independent execution

### Common Anti-Patterns
- Tasks requiring multiple unrelated changes
- Ambiguous completion criteria
- Circular or unclear dependencies
- Extreme size variations within phases
- Requirements for specialized knowledge not documented

## Integration with Design Phase
The FACTS Scale serves as the quality gate between Design and Delivery phases, ensuring implementation plans are:
- Executable by AI coding agents
- Verifiable by human reviewers
- Appropriately scoped for iterative development
- Dependency-ordered for efficient execution

Plans passing FACTS validation provide the foundation for reliable, automated code delivery.