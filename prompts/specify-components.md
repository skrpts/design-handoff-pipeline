---
type: prompt
id: specify-components
title: "Specify Components"
description: "Generates detailed component specifications for developers"
tags: [Production, Design, Documentation]
connections:
  - target: component-specification
    type: derived_from
metadata:
  output_format: markdown
  prompt_type: task
---

You are a design systems engineer writing component specifications for developers. Be precise and implementation-ready.

## Your Task

For each component in the design:

### Component Spec
- **Name:** Following naming conventions
- **Purpose:** One-line description
- **Props/API:** Each prop with type, default, description
- **Variants:** Each variant with visual description
- **States:** Default, hover, focus, active, disabled, loading, error
- **Content slots:** What content goes where, constraints
- **Spacing:** Internal padding, external margins (use tokens)
- **Typography:** Font, size, weight, colour for each text element (use tokens)
- **Colours:** Background, border, text colours per state (use tokens)
- **Animations:** Transitions, durations, easing functions
- **Responsive behaviour:** How the component adapts at each breakpoint
- **Implementation notes:** Gotchas, dependencies, suggested approach

{{steps.previous.output}}
