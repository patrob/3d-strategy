---
allowed-tools: Task, Read, Write, Bash
argument-hint: [Problem statement]
description: Research a problem using codebase and web search agents, compile findings into comprehensive research document
---

# Research Problem Statement

Launch parallel research agents to investigate the problem statement from both codebase and web perspectives, then compile findings into a comprehensive research document following RPI Strategy Research phase standards.

## Variables

PROBLEM_STATEMENT = $ARGUMENTS
SHORT_NAME = kebab-case version of problem statement (e.g., "Fix login authentication bug" → "fix-login-authentication-bug")
OUTPUT_DIR = ./rpi/SHORT_NAME/
OUTPUT_FILE = ./rpi/SHORT_NAME/research.md

## Task Overview

This command executes the Research phase of the RPI Strategy by:

1. **Parallel Codebase Research**: Launch three specialized codebase agents simultaneously
   - @agent-codebase-locator: Find WHERE relevant code exists
   - @agent-codebase-analyzer: Understand HOW the code works
   - @agent-codebase-pattern-finder: Discover similar implementations and patterns

2. **Parallel Web Research**: Launch web search agent simultaneously
   - @agent-web-search-researcher: Find Factual, Actionable, and Relevant external information

3. **Synthesis**: Compile all findings into a structured research document
   - Follow RPI Strategy Research phase output format
   - Include FAR Scale validation
   - Output to ./rpi/[short-name]/research.md

## Step 1: Launch All Research Agents in Parallel

You MUST launch all four agents in a single message using multiple Task tool calls. This ensures parallel execution:

### Codebase Locator Agent
**Agent**: codebase-locator
**Task**: "Locate all files, directories, and components relevant to: {PROBLEM_STATEMENT}. Focus on:
- Implementation files (core logic)
- Test files (unit, integration, e2e)
- Configuration files
- Type definitions/interfaces
- Related documentation
- Similar features or patterns

Return structured results grouped by purpose with full file paths."

### Codebase Analyzer Agent
**Agent**: codebase-analyzer
**Task**: "Analyze the implementation details for: {PROBLEM_STATEMENT}. Focus on:
- Entry points and public interfaces
- Core implementation logic
- Data flow and transformations
- State management
- Error handling
- Configuration usage
- Key architectural patterns

Provide detailed analysis with file:line references for all claims."

### Codebase Pattern Finder Agent
**Agent**: codebase-pattern-finder
**Task**: "Find existing code patterns and examples related to: {PROBLEM_STATEMENT}. Focus on:
- Similar implementations in the codebase
- Reusable patterns and conventions
- Test patterns for similar features
- Integration patterns
- Best practices already in use

Provide concrete code examples with file:line references."

### Web Search Researcher Agent
**Agent**: web-search-researcher
**Task**: "Research external information about: {PROBLEM_STATEMENT}. Apply FAR Scale criteria (Factual, Actionable, Relevant) to all findings:

**Factual (≥4.0)**: Find evidence-based information with verifiable sources
- Official documentation for relevant frameworks/libraries
- Technical specifications and standards
- Benchmark data and performance metrics
- Known issues, bugs, or limitations

**Actionable (≥3.0)**: Find implementation guidance
- Code examples and tutorials
- API references and usage patterns
- Configuration guides
- Migration guides or upgrade paths

**Relevant (≥3.0)**: Focus on information directly applicable to the problem
- Solutions to similar problems
- Best practices for the specific use case
- Trade-offs and design decisions
- Common pitfalls and gotchas

Structure findings with:
- Source URLs and publication dates
- Relevance assessment for each finding
- Key quotes and technical details
- FAR score for overall research quality"

## Step 2: Wait for All Agents to Complete

All four agents will execute in parallel. Wait for completion of all agents before proceeding to synthesis.

## Step 3: Synthesize Findings into Research Document

Once all agents complete, compile their findings into a comprehensive research document following the RPI Strategy Research phase format.

### Research Document Structure

Create `./rpi/SHORT_NAME/research.md` with the following mandatory sections:

```markdown
# [Problem Statement] Research

## Problem Context
- Restated, clarified problem statement
- Business/functional intent
- Current vs desired behavior
- Constraints (time, performance, compliance, environment)

[Synthesize from all agent findings to provide comprehensive context]

## Affected Files
```
[List files from codebase-locator findings]
[One reference per line using code reference syntax]
[path/to/file.ext:LINE or path/to/file.ext:START-END]
```

[Provide explanatory prose as bullet points beneath the code block]

## Code Examples
[Include minimal, relevant snippets from codebase-analyzer and codebase-pattern-finder]
[Show analogous patterns already in the codebase]
[Use triple backtick code fences, label language]

## External Research Findings
[Synthesize web-search-researcher findings]
[Include key insights, documentation references, best practices]
[Cite sources with URLs]

## FAR Scale Output

### Factual Score: [1-5]
[Evidence-based assessment with verifiable code/web references]

### Actionable Score: [1-5]
[Clear next steps identified from research]

### Relevant Score: [1-5]
[Solution addresses core problem and constraints]

### Mean: [calculated]
### Result: [PASS if mean ≥4.0, FAIL otherwise]

[If FAIL: Document what additional research is needed]

## Testing Strategy
Early hypotheses about:
- Unit test touchpoints [from codebase analysis]
- Integration/contract surfaces
- Observability (logs, metrics, traces)
- Repro steps if defect
- Risk areas needing characterization tests

## Potential Design Pattern Recommendations
[From codebase-pattern-finder and web research]
[Candidate patterns with rationale and internal exemplars]

## Assumptions
[Enumerated, falsifiable statements]
[Each should be testable or confirmable later]

## Out of Scope
[Explicit exclusions to prevent scope creep]
[Subsystems, refactors, deferred concerns]
```

## Step 4: Create Output Directory and Write Research Document

1. Create the output directory if it doesn't exist: `mkdir -p ./rpi/SHORT_NAME/`
2. Write the synthesized research document to `./rpi/SHORT_NAME/research.md`
3. Report completion with the file path

## Quality Gates

Before completing, verify:
- All four agents completed successfully
- Every code reference resolves (exists + line within bounds)
- No snippet exceeds ~40 lines unless justified
- All assumptions have validation steps or deferral notes
- FAR table present with numeric values + computed mean
- Output file created at correct path
- Research document follows mandatory section structure

## Expected Outcome

A comprehensive research document at `./rpi/SHORT_NAME/research.md` that:
- Combines codebase analysis with external research
- Provides validated, FAR-qualified findings
- Follows RPI Strategy Research phase standards
- Enables confident progression to Plan phase

## Notes

- The short-name should be derived from the problem statement using kebab-case
- Keep it concise but descriptive (e.g., "user-authentication-timeout" not "fix-the-bug-where-users")
- All agent tasks run in parallel for efficiency
- Synthesis should integrate findings, not just concatenate them
- Apply critical thinking when assessing FAR scores
