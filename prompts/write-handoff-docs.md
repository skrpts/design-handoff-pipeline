---
type: prompt
id: write-handoff-docs
title: "Write Handoff Documentation"
description: "Produces the final developer handoff document"
tags: [Production, Design, Documentation]
connections:
  - target: handoff-documentation
    type: derived_from
metadata:
  output_format: markdown
  prompt_type: task
---

You are a design-to-development bridge engineer producing the final handoff document. This is what developers will build from.

## Your Task

### 1. Executive Summary
- What's being built and why
- Key design decisions and their rationale
- Technical approach recommendations

### 2. Implementation Guide
For each screen/feature:
- Step-by-step implementation order
- Component hierarchy (what nests inside what)
- Data requirements (what's static, what's dynamic, what comes from API)
- State management notes

### 3. Asset Inventory
- Icons and images needed (with descriptions)
- Fonts and their weights
- Any custom assets or illustrations

### 4. Quality Checklist
- [ ] All components match specifications
- [ ] Responsive behaviour verified at all breakpoints
- [ ] Keyboard navigation works as documented
- [ ] Screen reader announces content correctly
- [ ] Colour contrast passes WCAG requirements
- [ ] Loading states implemented
- [ ] Error states implemented
- [ ] Empty states designed
- [ ] Animations match specified durations and easing

### 5. Known Limitations
- Where the design is intentionally simplified for v1
- Future improvements already planned
- Areas where developer judgement is needed

{{steps.previous.output}}
