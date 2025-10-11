---
allowed-tools: Read
argument-hint: [plan.md file]
description: Validate a plan against the FACTS rubric and return score, pass/fail status, and recommendations
---

## Variables

PLAN_FILE = $ARGUMENTS
RUBRIC_FILE = https://raw.githubusercontent.com/patrob/rpi-strategy/main/docs/scales/facts-scale.md

## Gather Context
- Read plan file !`cat PLAN_FILE`
- Fetch FACTS rubric from: RUBRIC_FILE

# Validate Plan Against FACTS Rubric

You are tasked with evaluating a technical implementation plan against the FACTS Scale rubric to determine if it meets quality standards for proceeding to the Implement phase.

## Your Task

1. **Read and Understand the Plan**: Review all tasks in the provided plan file to understand the implementation approach, task breakdown, and execution strategy.

2. **Read and Understand the FACTS Rubric**: Study the FACTS Scale scoring criteria from the rubric file, including:
   - **F**easibility: Can this be implemented with available resources? (0-5)
   - **A**tomicity: Is this task focused on a single responsibility? (0-5)
   - **C**larity: Is the execution order and dependencies clear? (0-5)
   - **T**estability: Can completion be verified? (0-5)
   - **S**ize: Is the task appropriately scoped? (0-5)

3. **Evaluate Each Task**: For each task in the plan, assign a score (0-5) for each FACTS dimension based on the rubric criteria.

4. **Calculate Mean Score**:
   - Calculate the arithmetic mean of all five dimensions (F, A, C, T, S)
   - Round to exactly 2 decimal places
   - Pass threshold: Mean >= 3.00

5. **Determine Pass/Fail Status**:
   - **PASS**: Mean score >= 3.00 AND all individual scores are reasonable
   - **FAIL**: Mean score < 3.00 OR any critical dimension fails (e.g., F < 3 indicates infeasible tasks)

6. **Provide Structured Output**:

### For PASS Status:
```
FACTS VALIDATION RESULT
=======================

Overall Assessment: PASS ✓

FACTS Scores:
F: [score]  A: [score]  C: [score]  T: [score]  S: [score]  Mean: [X.XX]  --> PASS

Summary:
[Brief explanation of why the plan passes, highlighting strengths]

The plan meets quality standards and is ready to proceed to the Implement phase.
```

### For FAIL Status:
```
FACTS VALIDATION RESULT
=======================

Overall Assessment: FAIL ✗

FACTS Scores:
F: [score]  A: [score]  C: [score]  T: [score]  S: [score]  Mean: [X.XX]  --> FAIL

Failure Classification:
[MINOR / MAJOR / CRITICAL based on mean score]
- Minor (2.8-2.9): Single iteration task refinement needed
- Major (2.0-2.7): Return to Research phase for problem decomposition
- Critical (<2.0): Leadership escalation required

Failure Reason:
[Explain why the plan failed - mean below 3.00 or specific dimension issues]

Recommendations to Improve:

1. **[Dimension Name]** (Current: [score], Target: >= 3)
   - Issue: [Specific problem identified]
   - Recommendation: [Concrete action to improve]

2. **[Dimension Name]** (Current: [score], Target: >= 3)
   - Issue: [Specific problem identified]
   - Recommendation: [Concrete action to improve]

[Continue for all failing dimensions]

Next Steps:
- **Minor Failure**: Refine task descriptions, adjust estimates, re-validate with /validate-plan
- **Major Failure**: Return to Research phase for missing context or problem decomposition
- **Critical Failure**: Escalate to technical lead, consider problem unfeasible with current approach
```

## Important Guidelines

- **Be Objective**: Score based strictly on the rubric criteria, not personal preferences
- **Be Specific**: Cite specific tasks or sections from the plan when identifying issues
- **Be Constructive**: Frame recommendations as actionable improvements
- **Be Precise**: Calculate mean to exactly 2 decimal places
- **Do NOT Create Files**: Return all output directly to the user - do not create any documents
- **Focus on Task Quality**: Evaluate whether tasks are well-defined, appropriately scoped, and executable

## Failure Severity Guidelines

**Minor Failure (Mean 2.8-2.9):**
- Plan is close to passing
- Single iteration refinement likely sufficient
- Focus on task description clarity and scoping adjustments

**Major Failure (Mean 2.0-2.7):**
- Significant gaps in plan quality
- May need additional research or problem decomposition
- Return to Research phase for enhanced context

**Critical Failure (Mean <2.0):**
- Fundamental issues with feasibility or approach
- Escalate to technical leadership
- Consider problem unfeasible with current approach or resources

The FACTS Scale ensures that plans are executable, maintainable, and set up for successful implementation.
