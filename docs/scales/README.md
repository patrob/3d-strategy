# Validation Scales Overview

This directory contains the centralized validation scales used throughout the RPI Strategy phases. Each scale provides specific scoring criteria for validating different aspects of the development process.

## FAR Scale (Research Phase)

**Purpose**: Validate code and implementation decisions during the Research phase
- **Usage**: Code-focused validation and evidence gathering
- **Dimensions**: Factual, Actionable, Relevant
- **Scoring**: 0-5 scale for each dimension
- **Pass Criteria**: F >= 4, A >= 3, R >= 3, Mean(F,A,R) >= 4.00
- **Threshold**: Pass required for phase completion

The FAR Scale ensures that Research phase findings are based on solid evidence, provide clear next steps, and address the core problem at hand.

For detailed scoring criteria and examples, see [far-scale.md](./far-scale.md).

## FACTS Scale (Plan Phase)

**Purpose**: Validate planning decisions and technical implementation plans
- **Usage**: Plan phase task breakdown validation
- **Dimensions**: Feasibility, Atomicity, Clarity, Testability, Size
- **Scoring**: 0-5 scale for each dimension
- **Pass Criteria**: Mean(F,A,C,T,S) >= 3.00
- **Threshold**: Pass required for phase completion

The FACTS Scale ensures that Plan phase outputs create actionable, well-scoped tasks that can be successfully executed in the Implement phase.

For detailed scoring criteria and examples, see [facts-scale.md](./facts-scale.md).

## Usage Guidelines

1. **Apply appropriate scale**: Use FAR for Research validation, FACTS for Plan validation
2. **Scoring precision**: All scores calculated to 2 decimal places (no additional rounding)
3. **Failure handling**: On validation failure, restart the respective phase workflow
4. **Actor responsibility**: Validation performed by phase-specific agents with optional human override
5. **Documentation**: Each validation must include scoring table and pass/fail decision

## Cross-References

- Research phase conceptual guidance: [../phases/Research.md](../phases/Research.md)
- Plan phase conceptual guidance: [../phases/Plan.md](../phases/Plan.md)