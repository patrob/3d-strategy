# Implement

## Purpose
Execute the validated technical implementation plan from the Plan phase by systematically completing atomic tasks, ensuring code quality at each step, and producing production-ready code that meets all specifications. Goal: transform the FACTS-qualified task breakdown into working, tested, and deployable code.

## Primary Objective
Execute the Plan phase output by:
- Implementing each atomic task in proper sequence or parallel groupings.
- Validating build, lint, and test success after each task completion.
- Tracking progress through checkbox completion in the design document.
- Maintaining code quality standards throughout implementation.
- Producing a fully functional solution ready for deployment.

## Input Artifact
Location: thoughts/[problem-short-name]/design.md
Requirements: Must have passed FACTS Scale validation (Mean >= 3.00)

## Output
No output artifact under normal execution.
- Tasks in design.md marked complete (`- [ ]` -> `- [x]`)
- Implemented, tested, production-ready code
- All build, lint, and test suites passing

## Failure Handling

Implement phase failures are classified and handled according to task execution outcomes:
- **Minor Failure**: Individual task quality gate failures (build/lint/test)
- **Major Failure**: 2+ consecutive task failures or critical path blocked with no clear resolution
- **Critical Failure**: 3+ consecutive failures, security issues, or extended blocks without resolution

**Quality Gates**: Each task must pass build → lint → test before completion. Failed gates trigger appropriate failure response.

**Catastrophic Failure Output**: Critical failures generate implement-postmortem.md at thoughts/[problem-short-name]/implement-postmortem.md

For complete failure handling procedures, escalation timelines, recovery paths, and postmortem requirements, see: [Failure Handling Framework](../README.md#failure-handling-framework)

## Task Execution Strategy

### Serial Execution (Primary Approach)
Execute tasks sequentially as listed in design.md. Each task must complete successfully before proceeding to the next. This ensures:
- Clear progress tracking
- Immediate issue identification
- No compounding errors
- Simpler debugging when issues arise

> **Parallel Execution Note:** Tools like Claude Code can execute independent tasks simultaneously using sub-agents. Tasks marked with `[P]` in the same phase can run in parallel if they affect different files and have no shared dependencies. Maximum 5 parallel tasks at once.

### Task Identification
- Tasks are defined as checkbox items in design.md
- Format: `- [ ] Task description`
- Phase boundaries separate task groups
- Tasks within a phase are executed in order

### Dependency Management
- Respect phase boundaries - complete all tasks in a phase before proceeding
- Within a phase, honor explicit dependencies noted in design.md
- Each task builds on the successful completion of the previous task

### Quality Gates
After each task completion (except "Red" phase of TDD):
1. **Build** must compile/run without errors
2. **Lint** must pass with no violations
3. **Tests** must pass with no failures
4. Update task checkbox to complete (- [x])

If any quality gate fails:
- Fix issues before proceeding to next task
- Do not mark task complete until all gates pass
- Document persistent blockers in postmortem if unresolvable

## Implementation Workflow

### Pre-Execution Validation
1. Verify design.md exists at expected location
2. Confirm FACTS Scale validation passed
3. Parse task breakdown and identify phases
4. Validate all referenced files are accessible

### Task Execution Loop
For each phase in design.md:
1. Identify all tasks in current phase
2. Execute tasks sequentially
3. For each task:
   - Implement specified changes
   - Run build → lint → test pipeline
   - Mark complete only if all pass
   - Handle failures per quality gates
4. Proceed to next phase only when all current phase tasks complete

> **Parallel Execution Note:** When using tools with sub-agent capabilities, tasks marked `[P]` can be batched and executed simultaneously, then results aggregated before proceeding.

### Completion Tracking
- Real-time updates to design.md checkboxes
- Each successful task: `- [ ]` -> `- [x]`
- Failed tasks remain unchecked with noted blockers
- Progress visible through design.md state


## Implementation Workflow Diagram
```mermaid
flowchart TD
  A([Start: Plan Document]) --> B[Parse Task List]
  B --> C[Select Next Task]
  C --> D[Implement Task]
  D --> E[Run Quality Gates<br/>Build → Lint → Test]
  E --> F{Quality Gates Pass?}
  F -- Yes --> G[Mark Task Complete]
  F -- No --> H[Apply Failure Handling<br/>Per Centralized Framework]
  H --> I{Continue or Escalate?}
  I -- Continue --> E
  I -- Escalate --> J[Return to Plan/Research<br/>or Generate Postmortem]
  G --> K{More Tasks?}
  K -- Yes --> C
  K -- No --> L[Done: Implement Complete]
```

*For detailed failure criteria, escalation procedures, and recovery paths, see [Failure Handling Framework](../README.md#failure-handling-framework)*

### Parallel Execution with Sub-Agents
> **Note:** When using tools like Claude Code that support sub-agents, the workflow can be modified to execute independent tasks in parallel:
>
> 1. Identify tasks marked with `[P]` in the current phase
> 2. Launch up to 5 sub-agents simultaneously
> 3. Each agent executes its task and runs quality gates
> 4. Aggregate results when all agents complete
> 5. Mark all successful tasks as complete
> 6. Handle any failures before proceeding to the next phase
>
> This approach can significantly reduce delivery time for projects with many independent tasks while maintaining the same quality standards.

## Quality Assurance

### Continuous Validation
- Every task must pass build, lint, and tests before marking complete
- No accumulation of technical debt during delivery
- Immediate remediation of quality issues
- No proceeding with broken states

### Test Execution Requirements
- Run full test suite after each task (unless TDD "Red" phase)
- Include unit, integration, and e2e tests as defined
- New tests from Plan phase must be implemented and passing
- Regression tests must continue passing

### Code Standards
- Follow existing codebase conventions
- Maintain consistent formatting via linter
- Preserve architectural patterns
- No divergence from Plan specifications

## Postmortem Generation

When catastrophic failure occurs, generate implement-postmortem.md with:
- Clear identification of the failed task and phase
- Complete error details and system state at failure
- Root cause analysis
- Recommended solutions and next steps
- Context needed to restart the RPI Strategy process if required

## Anti-Goals
- Don't refactor beyond what's specified in the tasks
- Don't add features not in the task list
- Don't modify the Plan document except for checking off completed tasks
- Don't complete multiple phases unless specified to do so
- Don't skip quality gates even under time pressure
- Don't leave tasks partially implemented
- Don't proceed with failing tests
- Don't implement optimizations not in the Plan

## Handoff Contract Upon Completion
Implement phase completes with:
- All tasks in design.md marked complete with [x]
- All tests passing (unit, integration, e2e)
- Build successful with no errors
- Lint passing with no violations
- Code ready for deployment
- No uncommitted changes unless specified
- Documentation updates if specified in tasks

## Reference
Plan artifact: thoughts/[problem-short-name]/design.md
FACTS validation: [FACTS Scale for Plan](../scales/facts-scale.md)