---
allowed-tools: Task, Read, Write, Glob, Bash(mkdir*)
argument-hint: [research.md file]
description: Build a multi-phase implementation plan with atomic task checklists from research file
---

# Plan Implementation from Research

Transform research findings into actionable, atomic task plans that follow TDD principles and the RPI Strategy methodology.

## Variables

RESEARCH_FILE = $ARGUMENTS // Path to research.md file

## Validation

- Ensure RESEARCH_FILE exists and is readable
- Extract directory path from RESEARCH_FILE for output location

## Step 1: Analyze Research File

Use the **codebase-analyzer** agent to deeply analyze the research file:

**Agent**: codebase-analyzer
**Task**: Analyze the research file at RESEARCH_FILE and extract:
- Key decisions and conclusions
- Actionable recommendations
- Technical specifications and constraints
- Implementation requirements
- Dependencies and integration points
- Testing requirements
- Edge cases and gotchas

Focus on identifying concrete, implementable items that can be translated into atomic tasks.

## Step 2: Build Implementation Plan

Using insights from the analysis, create a comprehensive implementation plan with these requirements:

### Plan Structure

1. **Overview Section** (in every plan file)
   - Brief summary of what will be implemented
   - Link back to the research file
   - Key decisions from research
   - Overall approach and strategy

2. **Phase Organization**
   - Each phase should have ≤10 atomic tasks
   - If more than 10 tasks needed, break into additional phases
   - Phases should have clear, logical boundaries
   - Each phase should be independently accomplishable

3. **Task Format** (atomic tasks using `- [ ]` checklist format)
   - Each task must be atomic: a single CLI command, file creation, file edit, test run, etc.
   - Start with TDD workflow: write test first (red), implement (green), refactor
   - Format: `- [ ] Action: specific description`
   - Examples:
     - `- [ ] Create test file: tests/unit/rate_limiter_test.py`
     - `- [ ] Write failing test: test_rate_limit_exceeded_returns_429`
     - `- [ ] Run tests: pytest tests/unit/rate_limiter_test.py (expect failure)`
     - `- [ ] Create file: src/middleware/rate_limiter.py`
     - `- [ ] Edit: Add RateLimiter class with check_limit() method`
     - `- [ ] Run tests: pytest tests/unit/rate_limiter_test.py (expect pass)`
     - `- [ ] Refactor: Extract sliding window logic to separate function`
     - `- [ ] Run command: npm install express-rate-limit`

4. **Context Per Phase**
   - Include just enough context to accomplish the phase
   - Reference relevant code files or documentation
   - Note key constraints or requirements
   - Highlight integration points or dependencies
   - Include test strategy for the phase

5. **TDD Workflow Priority**
   - Each feature should follow red/green/refactor cycle
   - Write test first (red)
   - Implement minimal code to pass (green)
   - Refactor for quality (refactor)
   - Include test execution steps explicitly

6. **Code References**
   - List all files that will be created or modified
   - Use fenced code block with file paths

7. **Testing Plan**
   - Overall testing strategy for the implementation
   - Test coverage expectations
   - Integration test requirements

8. **Dependencies & Sequencing**
   - External dependencies or packages needed
   - Phase execution order and dependencies
   - Parallel execution opportunities (mark with `[P]`)

9. **Risk Mitigation**
   - Potential blockers or challenges
   - Mitigation strategies
   - Fallback approaches

10. **Rollback Strategy**
    - How to undo changes if implementation fails
    - Database migration rollback if applicable
    - Feature flag approach if relevant

11. **Optional: Abbreviated FACTS Self-Check**
    - Quick self-assessment against FACTS criteria (not formal validation)
    - Helps identify obvious gaps before formal validation
    - Note: Formal FACTS validation happens via `/validate-plan` command

### Output Location

Create single file `plan.md` in same directory as RESEARCH_FILE.

The plan should use H2 headings (##) to organize phases within the single file.

### Plan Content Guidelines

- **Be specific**: No vague tasks like "implement feature" - break it down
- **Be atomic**: Each task should be one clear action
- **Be testable**: Include verification/test steps
- **Be ordered**: Tasks should flow logically, TDD workflow
- **Include commands**: Show exact CLI commands where applicable
- **Reference files**: Include file paths for edits/creations
- **Note dependencies**: Make inter-task dependencies clear

## Example Plan Structure

```markdown
# Implementation Plan: [Feature Name]

**Research**: [Link to research.md]
**Created**: [Date]

## Overview

[Brief summary of implementation]

### Key Decisions
- [Decision 1 from research]
- [Decision 2 from research]

### Approach
[Overall implementation strategy]

---

## Phase 1: [Phase Name]

**Goal**: [What this phase accomplishes]

**Context**:
- [Relevant constraint or requirement]
- [Key file or integration point]

**Tasks**:
- [ ] Create test file: tests/feature_test.py
- [ ] Write failing test: test_basic_functionality
- [ ] Run tests: pytest tests/feature_test.py (expect failure)
- [ ] Create file: src/feature.py
- [ ] Edit: Implement basic Feature class
- [ ] Run tests: pytest tests/feature_test.py (expect pass)
- [ ] Refactor: Extract helper methods
- [ ] [P] Update documentation (can run parallel with Phase 2 setup)

---

## Phase 2: [Phase Name]

[Continue pattern...]

---

## Code References

```
Files to be created:
- tests/feature_test.py
- src/feature.py

Files to be modified:
- src/index.js (add feature import)
- README.md (update documentation)
```

## Testing Plan

- Unit tests for all Feature class methods
- Integration tests for API endpoints
- Target: 90% code coverage

## Dependencies & Sequencing

- No external dependencies required
- Phase 1 must complete before Phase 2
- Documentation updates can run in parallel (marked with `[P]`)

## Risk Mitigation

- **Risk**: Existing API might conflict with new feature
- **Mitigation**: Use feature flag for gradual rollout

## Rollback Strategy

- Remove feature flag to disable
- Revert migrations: `npm run migrate:rollback`

## FACTS Self-Check (Optional)

Quick assessment before formal validation:
- Feasibility: Tasks are atomic and achievable
- Actionability: Each task has clear action
- Completeness: All requirements from research covered
- Testability: Test strategy defined
- Specificity: No vague tasks

Note: Run `/validate-plan plan.md` for formal FACTS validation
```

## Important Guidelines

- **Atomic tasks only**: No compound tasks or vague descriptions
- **TDD first**: Prioritize test-driven development workflow
- **10 task limit**: Break phases if exceeding 10 tasks per phase
- **Clear boundaries**: Each phase should be self-contained where possible
- **Include verification**: Every implementation step should have corresponding test/verification
- **Mark parallel tasks**: Use `[P]` prefix for tasks that can run in parallel with others
- **Be practical**: Tasks should map to actual commands, edits, or file operations
- **Preserve context**: Link back to research, note key decisions
- **Enable execution**: Someone should be able to follow the plan step-by-step
- **Single file**: Always output to single `plan.md` with H2 phase sections
- **Validation**: Include optional FACTS self-check; formal validation via `/validate-plan`

## Output Summary

After creating plan.md, provide a summary:
- Number of phases created
- File path of created plan
- Total number of atomic tasks
- Brief overview of implementation approach
- Key insights from research analysis
- Reminder to run `/validate-plan plan.md` for formal FACTS validation
