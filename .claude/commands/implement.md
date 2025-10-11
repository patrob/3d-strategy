---
allowed-tools: Task, Read, Grep, Glob, Bash
argument-hint: [plan.md file] [optional: all]
description: Implement tasks from a plan file, one at a time or all at once
---

## Variables

PLAN_FILE = $ARG1 // The plan.md file containing tasks to implement
IMPLEMENT_ALL = $ARG2 // Optional flag "all" to implement all tasks without returning

## Gather Context
- Read the plan file: !`cat "$PLAN_FILE"`

# Implement Plan Tasks

You are implementing tasks from a plan file. The plan file contains a list of tasks with checkboxes indicating completion status.

## Your Responsibilities

### 1. Parse the Plan File
- Identify all tasks in the plan file (look for checkbox patterns like `- [ ]` or `- [x]`)
- Determine which tasks are complete (`[x]`) and which are incomplete (`[ ]`)
- Extract any context, dependencies, or requirements mentioned in the plan

### 2. Fetch Required Context
- Scan the plan file for references to other files, directories, or components
- Use Grep and Glob tools to locate relevant code files
- Read any files that provide necessary context for implementation
- Understand the codebase structure and existing patterns

### 3. Determine Execution Mode

**Single Task Mode (default):**
- If IMPLEMENT_ALL is not "all", implement only the NEXT unchecked task
- After completing the task, return to user for validation
- Do NOT proceed to subsequent tasks

**All Tasks Mode (when IMPLEMENT_ALL = "all"):**
- Implement EVERY unchecked task in the plan file
- Continue through all tasks without returning to user
- Provide comprehensive summary at the end

### 4. Task Execution Process

For each task to implement:

**a) Implement the Task:**
- Make the necessary code changes
- Follow existing code patterns and conventions
- Ensure the implementation matches the task requirements
- Handle edge cases and error conditions
- Respect phase boundaries (complete all tasks in a phase before proceeding)
- Identify parallel tasks marked with `[P]` prefix

**b) Run Quality Gates:**
After implementation, run in sequence:
1. **Build** - Project must compile/build successfully
2. **Lint** - Code must pass linting checks
3. **Test** - All tests must pass

Note: Skip quality gates during TDD "Red" phase (when test is expected to fail)

**c) Update Plan File:**
- Mark the completed task as done by changing `- [ ]` to `- [x]`
- Preserve all plan metadata (FACTS scores, sections, etc.)
- Do not modify other content in the plan file

### 5. Quality Gates & Failure Classification

Run appropriate project commands: build → lint → test

**Failure Classification:**
- **Minor**: Single test failure, fixable in current session - fix and retry immediately
- **Major**: Multiple test failures, build breaks, lint errors requiring rework - stop and report to user
- **Critical**: 3+ consecutive major failures, fundamental design flaw, security issue - stop and output postmortem to user

**On Failure:**
- Stop execution immediately
- Report complete error output
- Do NOT mark task as complete
- Do NOT proceed to next task

**Postmortem Output (Critical Failures):**
When catastrophic failure occurs, output to user:
- Failed task and phase context
- Complete error details and system state
- Root cause analysis
- Recommended solutions and recovery paths

### 6. Reporting

**After Single Task (default mode):**
Provide:
- Summary of what was implemented
- Which task was completed
- Results of all quality checks (tests, build, lint)
- Any issues or considerations
- Updated plan file status

**After All Tasks (all mode):**
Provide:
- Comprehensive summary of all tasks completed
- Any tasks that could not be completed and why
- Overall quality check results
- Final plan file status
- Recommendations for next steps

## Special Considerations

- **Parallel Tasks:** Tasks marked with `[P]` can run concurrently if they affect different files with no shared dependencies
- **Phase Boundaries:** Complete all tasks in a phase before starting next phase
- **Task Dependencies:** If a task depends on another unchecked task, implement dependencies first or report the blocker
- **Ambiguous Tasks:** If a task is unclear, document assumptions and note the ambiguity in the report
- **Failed Checks:** Never mark a task complete if quality gates fail
- **File Not Found:** If the plan file doesn't exist, report error clearly
- **No Tasks:** If all tasks are complete, report this and take no action

## Implementation Strategy

### For Single Task Mode:
1. Read and parse plan file
2. Identify the first unchecked task in current phase
3. Gather relevant context
4. Implement the task
5. Run quality gates (build → lint → test)
6. Update plan file
7. Report to user and STOP

### For All Tasks Mode:
1. Read and parse plan file
2. Get list of all unchecked tasks
3. For each unchecked task:
   a. Gather context
   b. Implement task
   c. Run quality gates
   d. If gates fail: classify failure, apply appropriate handling
   e. Update plan file
   f. Continue to next task (respecting phase boundaries)
4. Provide comprehensive final report

Begin implementation now based on the provided arguments.
