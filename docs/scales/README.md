# Validation Scales Overview

This directory contains the centralized validation scales used throughout the 3D Strategy phases. Each scale provides specific scoring criteria for validating different aspects of the development process.

## FAR Scale (Discovery Phase)

**Purpose**: Validate code and implementation decisions during the Discovery phase
- **Usage**: Code-focused validation and evidence gathering
- **Dimensions**: Factual, Actionable, Relevant
- **Scoring**: 0-5 scale for each dimension
- **Pass Criteria**: F >= 4, A >= 3, R >= 3, Mean(F,A,R) >= 4.00
- **Threshold**: Pass required for phase completion

The FAR Scale ensures that Discovery phase findings are based on solid evidence, provide clear next steps, and address the core problem at hand.

For detailed scoring criteria and examples, see [far-scale.md](./far-scale.md).

## FACTS Scale (Design Phase)

**Purpose**: Validate design decisions and technical implementation plans
- **Usage**: Design phase task breakdown validation
- **Dimensions**: Feasibility, Atomicity, Clarity, Testability, Size
- **Scoring**: 0-5 scale for each dimension
- **Pass Criteria**: Mean(F,A,C,T,S) >= 3.00
- **Threshold**: Pass required for phase completion

The FACTS Scale ensures that Design phase outputs create actionable, well-scoped tasks that can be successfully executed in the Delivery phase.

For detailed scoring criteria and examples, see [facts-scale.md](./facts-scale.md).

## Usage Guidelines

1. **Apply appropriate scale**: Use FAR for Discovery validation, FACTS for Design validation
2. **Scoring precision**: All scores calculated to 2 decimal places (no additional rounding)
3. **Failure handling**: On validation failure, restart the respective phase workflow
4. **Actor responsibility**: Validation performed by phase-specific agents with optional human override
5. **Documentation**: Each validation must include scoring table and pass/fail decision

## Cross-References

- Discovery phase conceptual guidance: [../phases/Discovery.md](../phases/Discovery.md)
- Design phase conceptual guidance: [../phases/Design.md](../phases/Design.md)