---
allowed-tools: Task, Read, Grep, Glob
argument-hint: [specific-focus]
description: Critically analyze repository documentation for clarity, completeness, and actionable insights
---

# Analyze Repository Documentation

Launch the documentation-critic agent to perform a comprehensive critical analysis of this repository's documentation.

## Task for Documentation Critic Agent

You are to use the documentation-critic sub-agent to analyze all documentation in this repository (excluding the `.claude` folder). The agent should:

1. **Scan Documentation Files**: Find and analyze all documentation files including:
   - README.md files at all levels
   - Documentation in `/docs` or similar folders
   - Inline documentation in code files
   - Configuration documentation
   - Any markdown files providing guidance

2. **Perform Critical Analysis**: Apply the documentation critic framework to evaluate:
   - **Clarity**: Identify ambiguous language, unclear explanations, undefined jargon
   - **Redundancy**: Find duplicate or repetitive content that adds no value
   - **Completeness**: Detect missing context, examples, or error handling documentation
   - **Structure**: Assess organization, navigation, and discoverability
   - **Actionability**: Evaluate if documentation enables immediate practical application

3. **Focus Areas** (if specified): $ARGUMENTS

4. **Provide Structured Report** with:
   - Executive summary of documentation quality
   - Categorized issues by severity (Critical, High, Medium, Low)
   - Specific improvement recommendations with rationale
   - Recognition of effective documentation practices
   - Prioritized action plan for improvements

## Expected Output Format

The agent should produce a comprehensive report that:
- Cites specific files and line numbers
- Provides evidence for each critique
- Offers concrete, actionable improvements
- Explains the reasoning behind each recommendation
- Helps repository maintainers understand how to make their documentation more helpful, clear, and actionable as a reference implementation

## Agent Configuration

Launch the documentation-critic agent with:
- Focus: Critical but constructive analysis
- Goal: Improve documentation quality for better developer experience

Begin by discovering all documentation files, then systematically analyze each for the criteria above. Exclude the `.claude` folder from analysis.

Output documentation in a file `./thoughts/docs-analysis.md`