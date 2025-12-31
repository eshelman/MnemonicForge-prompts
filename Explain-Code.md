---
schema_version: 1
title: Explain Code
description: Get clear explanations of code snippets tailored to your experience level
tags:
  - development
  - learning
  - code
parameters:
  - name: experience_level
    type: enum
    label: Your Experience Level
    options:
      - Beginner (new to programming)
      - Intermediate (comfortable with basics)
      - Advanced (want technical depth)
    default: Intermediate (comfortable with basics)
  - name: focus_area
    type: enum
    label: Explanation Focus
    options:
      - General Overview
      - Line-by-Line Walkthrough
      - Logic and Algorithm
      - Best Practices Review
      - Security Considerations
    default: General Overview
  - name: language_hint
    type: string
    label: Programming Language (if not obvious)
    required: false
  - name: specific_questions
    type: text
    label: Specific Questions (optional)
    required: false
    multiline: true
model:
  provider: openai
  name: gpt-4o
  temperature: 0.3
  max_tokens: 2500
preferred_clipboard_types:
  - text
---
Explain the following code.

**Experience Level:** {{experience_level}}
**Focus:** {{focus_area}}
{{#if language_hint}}
**Language:** {{language_hint}}
{{/if}}

{{#if specific_questions}}
**Specific Questions:**
{{specific_questions}}
{{/if}}

Please structure your explanation to match my experience level and focus area. Include:
- What the code does at a high level
- Key concepts or patterns used
- Details specific to the selected focus area
- How I might use or modify this code

---

```
{{clipboard}}
```
