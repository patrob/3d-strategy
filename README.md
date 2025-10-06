# RPI Strategy for Agentic Engineering

A framework for delivering software at scale using AI coding agents through a disciplined **Research > Plan > Implement** approach.

## Overview

This repository documents the RPI Strategy methodology for engineering teams working with AI coding agents. The three-phase approach provides a repeatable discipline for successfully delivering software projects while leveraging the capabilities of modern AI development tools.

**Research > Plan > Implement** forms the core framework for:
- Understanding requirements and constraints
- Architecting solutions with AI assistance
- Implementing and deploying with confidence

## What's Included

- Documentation of the RPI Strategy methodology
- **Example workflows** for popular AI coding tools:
  - **Claude Code**: `"Analyze the authentication bug in user/session.py:245. Use Research phase: identify problem scope, validate with FAR scale ≥4.0, then plan atomic fixes."`
  - **GitHub Copilot**: Use structured comments like `// RESEARCH: User login fails intermittently - need factual evidence from logs` before requesting code suggestions
  - **Cursor**: Apply FACTS scale validation to generated task breakdowns: "Validate this implementation plan using FACTS scale - is each task <4hrs and independently testable?"

## Documentation Structure

### Core Framework
- **[RPI Strategy Phases](docs/phases/README.md)** - Complete guide to Research → Plan → Implement
  - [Research Phase](docs/phases/Discovery.md) - Build context & insight
  - [Plan Phase](docs/phases/Design.md) - Decide what to do & how
  - [Implement Phase](docs/phases/Implement.md) - Ship & learn

### Quality Framework
- **[Validation Scales](docs/scales/README.md)** - Improve GenAI and human results using structured validation
  - [FAR Scale](docs/scales/far-scale.md) - Factual, Actionable, Relevant scoring
  - [FACTS Scale](docs/scales/facts-scale.md) - For comprehensive design validation

## Quick Start (5 minutes)

**Try this now** with your next AI coding task:

1. **Research**: Before asking for code, prompt: *"Help me understand the problem scope first. What's the specific issue, where in the codebase, and what evidence supports this?"*

2. **Validate**: Score your findings using [FAR scale](docs/scales/far-scale.md): Factual ≥4, Actionable ≥3, Relevant ≥3

3. **Plan**: Request: *"Break this into atomic tasks (single command calls, file edits, etc.). Validate each task is testable independently."*

4. **Validate**: Check tasks against [FACTS scale](docs/scales/facts-scale.md): Mean ≥3.0 across all dimensions

5. **Implement**: Execute one task, measure results, iterate

**Example**: Instead of *"Fix the login bug"*, try: *"Research: User login fails on mobile Chrome. Evidence: 3 support tickets, error 'session undefined' in console logs. Validate this against FAR scale before planning solution."*

## Getting Started

1. Start with the [RPI Strategy Phases overview](docs/phases/README.md) to understand the Research → Plan → Implement framework
2. Apply the [Validation Scales](docs/scales/README.md) to improve the quality of your AI interactions and outputs
3. Explore phase-specific documentation and example prompts for your preferred AI coding environment

*Inspiration to work on this came from watching [this video](https://www.youtube.com/watch?v=IS_y40zY-hc).