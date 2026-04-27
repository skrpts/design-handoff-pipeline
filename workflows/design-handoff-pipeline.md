---
type: workflow
id: design-handoff-pipeline
title: Design-to-Developer Handoff Pipeline
description: "Review designs, generate component specs, define responsive requirements, audit accessibility, and produce handoff documentation"
tags: [Production, Customer-Facing, Design, Handoff, Documentation]
connections:
  - target: design-review
    type: uses
  - target: component-specification
    type: uses
  - target: responsive-requirements
    type: uses
  - target: accessibility-audit
    type: uses
  - target: handoff-documentation
    type: uses
  - target: language-polish
    type: uses
  - target: consistency-check
    type: uses
  - target: llm-service
    type: runs_on
metadata:
  estimated_duration: "15-25 minutes"
  trigger: manual
output_step: "language-polish"
composite_steps:
  - "design-review"
  - "component-specification"
  - "responsive-requirements"
  - "accessibility-audit"
  - "handoff-documentation"
  - "language-polish"
  - "consistency-check"
execution:
  - skill: "design-review"
    prompt: "review-design-decisions"
    step_type: "synthesis"
  - skill: "component-specification"
    prompt: "specify-components"
    step_type: "generation"
  - skill: "responsive-requirements"
    prompt: "define-responsive-requirements"
    step_type: "generation"
  - skill: "accessibility-audit"
    prompt: "audit-accessibility"
    step_type: "review"
  - skill: "handoff-documentation"
    prompt: "write-handoff-docs"
    step_type: "generation"
  - skill: "language-polish"
    prompt: "polish-language"
    step_type: "content"
  - parallel:
    - skill: "consistency-check"
      prompt: "check-consistency"
      step_type: "review"
---

## Overview

This workflow produces a complete design-to-developer handoff package: design decision review, component specifications, responsive requirements, accessibility audit, and implementation-ready documentation. The output is what developers need to build exactly what was designed.

## Pipeline Stages

### Stage 1: Design Review

**Input:** Design description, design decisions, target platforms, accessibility level

Invoke the **design-review** skill to establish context: design overview, decision audit, implementation considerations, and open questions.

**Output:** Design context document with decisions and technical flags.

### Stage 2: Component Specification

**Input:** Design review from Stage 1

Invoke the **component-specification** skill to produce detailed specs for each component: props, states, variants, spacing, typography, colours, and animations.

**Output:** Implementation-ready component specifications.

### Stage 3: Responsive Requirements

**Input:** Component specs from Stage 2

Invoke the **responsive-requirements** skill to document how layouts and components adapt across breakpoints.

**Output:** Responsive behaviour documentation with breakpoint-specific layouts.

### Stage 4: Accessibility Audit

**Input:** All previous specifications

Invoke the **accessibility-audit** skill to review against WCAG guidelines: contrast, keyboard navigation, screen reader support, and interaction patterns.

**Output:** Accessibility checklist with compliance status and recommendations.

### Stage 5: Handoff Documentation

**Input:** All previous stages

Invoke the **handoff-documentation** skill to produce the final developer handoff document with implementation guide, asset inventory, and quality checklist.

**Output:** Complete handoff package.

### Stage 6: Language Polish

Invoke **language-polish** for final cleanup.

### Stage 7: Consistency Check (Parallel)

Invoke **consistency-check** to verify token references and terminology are consistent across all specs.

## Error Handling

- If design description is brief, specs focus on what's described and flag gaps
- If no accessibility level is specified, defaults to WCAG 2.1 AA
- If no platform is specified, defaults to responsive web

## Inputs

| Name | Required | Description | Example |
|------|----------|-------------|---------|
| `{{input.design_description}}` | Yes | Designs to hand off | `New onboarding flow: 4 screens with wizard pattern` |
| `{{input.design_decisions}}` | No | Rationale behind key choices | `Wizard pattern chosen because research showed form overwhelm` |
| `{{input.target_platforms}}` | No | Where this will be built | `React web app with responsive mobile` |
| `{{input.accessibility_level}}` | No | WCAG compliance target | `WCAG 2.1 AA` |

## Outputs

| Name | Description |
|------|-------------|
| Design review | Context, decisions, technical considerations |
| Component specs | Detailed specs with props, states, variants |
| Responsive requirements | Breakpoint-specific layout documentation |
| Accessibility audit | WCAG compliance checklist and recommendations |
| Handoff documentation | Implementation guide and quality checklist |

## Setup

1. No external services required.
2. Describe your designs in as much detail as possible.
3. Include design decisions and rationale for better developer context.

## Provider Notes

- Component specification and accessibility audit benefit from stronger models.
- The five sequential stages build on each other — each adds a layer of detail.

## Example Input

```
Design Description: "New user onboarding flow for our project management SaaS. Four screens: (1) Welcome screen with value proposition and 'Get Started' CTA, (2) Profile setup — name, role dropdown, avatar upload, (3) Team creation — team name, invite members by email with role assignment (admin/member/viewer), (4) First project — project name, template selection (blank, marketing, engineering, product), due date picker. Animated slide transitions between screens. Progress bar at top showing steps 1-4. 'Skip' link on steps 2-4 that goes to dashboard with defaults. Confetti animation on completion."
Design Decisions: "Wizard pattern over single form — user research showed new users felt overwhelmed by too many fields at once. Skip option for power users who want to configure later. Role dropdown limited to 3 options to reduce decision fatigue. Template selection included because 68% of users who chose a template in beta had higher 30-day retention. Confetti on completion because our brand is playful and we want to celebrate the milestone."
Target Platforms: "React web app (Next.js), responsive down to 375px width. No native mobile app — mobile web must work well."
Accessibility Level: "WCAG 2.1 AA — we have enterprise customers with accessibility requirements in their procurement process"
```
