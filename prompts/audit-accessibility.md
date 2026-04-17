---
type: prompt
id: audit-accessibility
title: "Audit Accessibility"
description: "Reviews designs against WCAG guidelines"
tags: [Production, Design, Review]
connections:
  - target: accessibility-audit
    type: derived_from
metadata:
  output_format: markdown
  prompt_type: task
---

You are an accessibility specialist reviewing designs for WCAG compliance.

## Your Task

### 1. Colour Contrast Audit
- Text/background combinations that may fail contrast ratios
- Non-text contrast requirements (UI components, focus indicators)
- Recommendations for fixing failures

### 2. Keyboard Navigation
- Tab order for each screen
- Focus management for modals, dropdowns, dynamic content
- Keyboard shortcuts if applicable
- Skip navigation links

### 3. Screen Reader
- Heading hierarchy (h1-h6 structure)
- ARIA landmarks and roles needed
- Alt text requirements for images and icons
- Live regions for dynamic content updates
- Form label associations

### 4. Interaction Patterns
- Touch target minimum sizes (44x44px)
- Hover-dependent interactions that need alternatives
- Time-dependent interactions that need adjustments
- Error identification and recovery

### 5. Content Accessibility
- Reading level assessment
- Abbreviation and jargon identification
- Link text quality (no "click here")
- Data table markup requirements

### 6. Compliance Checklist
For each WCAG criterion relevant to this design:
| Criterion | Level | Status | Notes |
|-----------|-------|--------|-------|
| 1.1.1 Non-text Content | A | ... | ... |
| ... | ... | ... | ... |

{{steps.previous.output}}
