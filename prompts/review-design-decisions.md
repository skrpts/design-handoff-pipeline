---
type: prompt
id: review-design-decisions
title: "Review Design Decisions"
description: "Reviews design decisions and rationale to establish handoff context"
tags: [Production, Design, Review]
connections:
  - target: design-review
    type: derived_from
inputs:
  design_description:
    label: "Design Description"
    description: "Describe the designs to hand off — screens, components, interactions"
    example: "New user onboarding flow: 4 screens (welcome, profile setup, team creation, first project). Includes animated transitions between screens, a progress indicator, and skip option."
    required: true
    type: text
  design_decisions:
    label: "Design Decisions"
    description: "Rationale behind key design choices"
    example: "We chose a wizard pattern over a single form because user research showed new users feel overwhelmed by too many fields. The skip option exists because power users want to configure later."
    required: false
    type: text
  target_platforms:
    label: "Target Platforms"
    description: "Where this will be implemented"
    example: "React web app with responsive mobile support"
    required: false
    type: text
  accessibility_level:
    label: "Accessibility Level"
    description: "WCAG compliance target"
    example: "WCAG 2.1 AA"
    required: false
    type: text
---

You are a design lead reviewing designs before developer handoff. Establish the full context.

## Design Description
{{input.design_description}}

## Design Decisions
{{input.design_decisions}}

## Target Platforms
{{input.target_platforms}}

## Accessibility Target
{{input.accessibility_level}}

## Your Task

### 1. Design Overview
- Summary of what's being handed off
- User flow diagram (text-based)
- Key screens/states and their purpose

### 2. Design Decision Audit
For each significant design decision:
- What was decided
- Why (user research, business requirement, technical constraint)
- Alternatives considered
- Trade-offs accepted

### 3. Implementation Considerations
- Technical complexities to flag for developers
- Animation and transition specifications
- Edge cases and error states
- Content that needs to be dynamic vs static

### 4. Open Questions
- Decisions that still need resolution
- Areas where developer input is needed
- Dependencies on other teams or systems
