# 3D Strategy for Agentic Engineering

A framework for delivering software at scale using AI coding agents through a disciplined **Discovery > Design > Delivery** approach.

## Overview

This repository documents the 3D Strategy methodology for engineering teams working with AI coding agents. The three-phase approach provides a repeatable discipline for successfully delivering software projects while leveraging the capabilities of modern AI development tools.

**Discovery > Design > Delivery** forms the core framework for:
- Understanding requirements and constraints
- Architecting solutions with AI assistance
- Implementing and deploying with confidence

## What's Included

- Documentation of the 3D Strategy methodology
- **Example workflows** for popular AI coding tools:
  - **Claude Code**: `"Analyze the authentication bug in user/session.py:245. Use Discovery phase: identify problem scope, validate with FAR scale ≥4.0, then design atomic fixes."`
  - **GitHub Copilot**: Use structured comments like `// DISCOVERY: User login fails intermittently - need factual evidence from logs` before requesting code suggestions
  - **Cursor**: Apply FACTS scale validation to generated task breakdowns: "Validate this implementation plan using FACTS scale - is each task <4hrs and independently testable?"

## Documentation Structure

### Core Framework
- **[3D Strategy Phases](docs/phases/README.md)** - Complete guide to Discovery → Design → Delivery
  - [Discovery Phase](docs/phases/Discovery.md) - Build context & insight
  - [Design Phase](docs/phases/Design.md) - Decide what to do & how
  - [Delivery Phase](docs/phases/Delivery.md) - Ship & learn

### Quality Framework
- **[Validation Scales](docs/scales/README.md)** - Improve GenAI and human results using structured validation
  - [FAR Scale](docs/scales/far-scale.md) - Factual, Actionable, Relevant scoring
  - [FACTS Scale](docs/scales/facts-scale.md) - For comprehensive design validation

## Quick Start (5 minutes)

**Try this now** with your next AI coding task:

1. **Discovery**: Before asking for code, prompt: *"Help me understand the problem scope first. What's the specific issue, where in the codebase, and what evidence supports this?"*

2. **Validate**: Score your findings using [FAR scale](docs/scales/far-scale.md): Factual ≥4, Actionable ≥3, Relevant ≥3

3. **Design**: Request: *"Break this into tasks <4 hours each. Validate each task is testable independently."*

4. **Validate**: Check tasks against [FACTS scale](docs/scales/facts-scale.md): Mean ≥3.0 across all dimensions

5. **Delivery**: Execute one task, measure results, iterate

**Example**: Instead of *"Fix the login bug"*, try: *"Discovery: User login fails on mobile Chrome. Evidence: 3 support tickets, error 'session undefined' in console logs. Validate this against FAR scale before designing solution."*

## Getting Started

1. Start with the [3D Strategy Phases overview](docs/phases/README.md) to understand the Discovery → Design → Delivery framework
2. Apply the [Validation Scales](docs/scales/README.md) to improve the quality of your AI interactions and outputs
3. Explore phase-specific documentation and example prompts for your preferred AI coding environment