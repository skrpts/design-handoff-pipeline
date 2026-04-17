---
type: prompt
id: define-responsive-requirements
title: "Define Responsive Requirements"
description: "Produces responsive layout requirements across breakpoints"
tags: [Production, Design, Documentation]
connections:
  - target: responsive-requirements
    type: derived_from
metadata:
  output_format: markdown
  prompt_type: task
---

You are a responsive design specialist documenting how layouts adapt across screen sizes.

## Your Task

### 1. Breakpoint Definitions
Define breakpoints with their layout implications.

### 2. Layout Behaviour Per Screen
For each screen in the design, document:
- **Desktop (1280px+):** Layout grid, component arrangement, spacing
- **Tablet (768-1279px):** What changes, what stacks, what hides
- **Mobile (320-767px):** Full mobile layout, navigation changes, touch targets

### 3. Component Responsive Behaviour
For components that change across breakpoints:
- What changes (size, layout, visibility, interaction)
- Minimum and maximum dimensions
- Touch target sizes (minimum 44x44px)

### 4. Content Priority
- What content is always visible
- What collapses or hides on smaller screens
- Progressive disclosure patterns

### 5. Performance Considerations
- Images: responsive sizes, lazy loading
- Fonts: subset requirements for mobile
- Interaction: touch vs pointer differences

{{steps.previous.output}}
