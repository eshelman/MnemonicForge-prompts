---
schema_version: 1
title: Summarize Content
description: Condense long text into digestible summaries with customizable length and format
tags:
  - productivity
  - reading
  - research
parameters:
  - name: length
    type: enum
    label: Summary Length
    options:
      - Brief (2-3 sentences)
      - Standard (1 paragraph)
      - Detailed (multiple paragraphs)
    default: Standard (1 paragraph)
  - name: format
    type: enum
    label: Output Format
    options:
      - Prose
      - Bullet Points
      - Numbered List
    default: Bullet Points
  - name: focus
    type: string
    label: Focus Area (optional)
    required: false
model:
  provider: openai
  name: gpt-4o
  temperature: 0.3
  max_tokens: 1500
preferred_clipboard_types:
  - text
  - url
---
Summarize the following content.

**Length:** {{length}}
**Format:** {{format}}
{{#if focus}}
**Focus particularly on:** {{focus}}
{{/if}}

---

{{clipboard}}
