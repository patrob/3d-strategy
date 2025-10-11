---
allowed-tools: Read
argument-hint: [research.md file]
description: Validate research document against FAR (Factual, Actionable, Relevant) rubric
---

# Validate Research Against FAR Scale

Evaluate the provided research document against the FAR Scale rubric to determine if it meets the quality criteria required to proceed from the Research phase to the Plan phase.

## Variables

RESEARCH_FILE = $ARGUMENTS
RUBRIC_FILE = https://raw.githubusercontent.com/patrob/rpi-strategy/main/docs/scales/far-scale.md

## Gather Context

- Read the research document to validate: !`cat RESEARCH_FILE`
- Fetch FAR Scale rubric from: RUBRIC_FILE

## Task

You are a Research Agent evaluating research findings against the FAR Scale validation criteria. Your role is to:

1. **Analyze the Research Document**: Review the provided research.md file for:
   - Evidence quality (code references, traces, tests, reproduction steps)
   - Implementation readiness (concrete next steps, clear ownership, actionable plans)
   - Problem alignment (relevance to ticket/story, impact on acceptance criteria)

2. **Score Each FAR Dimension**: Using the rubric scoring scale (0-5), evaluate:

   **Factual (F)**: "Is this evidenced in the code/system?"
   - Look for: deterministic repro, code references, failing tests, traces, commit history
   - Strong evidence: >= 4 (corroborated or strongly verified)
   - Threshold: Must be >= 4 to pass

   **Actionable (A)**: "Can I move this forward now?"
   - Look for: concrete next steps, clear ownership, low-friction plan, specific files/functions
   - Implementation ready: >= 3 (concrete next step exists)
   - Threshold: Must be >= 3 to pass

   **Relevant (R)**: "Does it matter to this ticket/story now?"
   - Look for: blocks acceptance criteria, affects current sprint, customer impact
   - On-theme: >= 3 (within component/surface, affects acceptance criteria)
   - Threshold: Must be >= 3 to pass

3. **Calculate Mean Score**:
   - Mean = (F + A + R) / 3
   - Calculate to 2 decimal places (no additional rounding)
   - Threshold: Must be >= 4.00 to pass

4. **Determine Pass/Fail Status**:
   - **PASS** if ALL criteria met:
     - F >= 4
     - A >= 3
     - R >= 3
     - Mean >= 4.00
   - **FAIL** if ANY criterion not met

5. **Provide Recommendations** (if FAIL):
   - Identify which dimension(s) fell short
   - Cite specific gaps in the research document
   - Recommend concrete improvements to reach pass criteria
   - Reference rubric examples and scoring cues
   - Note: FAR is for research validation; FACTS Scale is used for plan validation (different rubrics)

## Output Format

Return your evaluation to the user in this format:

```
=== FAR SCALE VALIDATION ===

SCORES:
F: [score]  A: [score]  R: [score]  Mean: [X.XX]  --> [PASS/FAIL]

STATUS: [PASS/FAIL]

ANALYSIS:

Factual (F = [score]):
[Justify score with specific evidence from research document]

Actionable (A = [score]):
[Justify score with specific evidence from research document]

Relevant (R = [score]):
[Justify score with specific evidence from research document]

[If PASS:]
VERDICT: Research meets all FAR criteria. Ready to proceed to Plan phase.

NEXT STEP: Use this validated research.md as input to /plan command.

[If FAIL:]
VERDICT: Research does not meet FAR criteria.

FAILURE CLASSIFICATION:
- Minor (3.5-3.9): Additional targeted research needed
- Major (2.0-3.4): Restart Research phase for comprehensive investigation
- Critical (<2.0): Problem may be ill-defined or out of scope

RECOMMENDATIONS TO IMPROVE:
- [Specific recommendation 1 with rubric reference]
- [Specific recommendation 2 with rubric reference]
- [etc.]

NEXT STEP: Address recommendations and restart Research phase if needed.
```

## Important Guidelines

- **Be objective**: Base scores strictly on evidence present in the research document
- **Cite specifics**: Reference exact sections, code references, or gaps in the research
- **Apply rubric rigorously**: Use the scoring cues and examples from the FAR Scale
- **Don't create documents**: Only return evaluation to the user (do not write files)
- **Calculate precisely**: Mean score to exactly 2 decimal places
- **Be constructive**: If failing, provide actionable path to improvement
- **Note on rubrics**: FAR Scale validates research quality; FACTS Scale validates plan quality (used in /validate-plan)

## Failure Severity Guidelines

**Minor Failure (Mean 3.5-3.9):**
- Research is close to passing
- Additional targeted research in specific areas
- Quick iteration likely sufficient

**Major Failure (Mean 2.0-3.4):**
- Significant gaps in research depth or evidence
- Restart Research phase with clearer focus
- May need different research approach

**Critical Failure (Mean <2.0):**
- Fundamental issues with problem definition or relevance
- Consult with stakeholders on problem scope
- Problem may be out of scope or ill-defined

Begin your validation now.
