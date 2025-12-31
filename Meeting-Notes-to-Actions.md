---
schema_version: 1
title: Meeting Notes to Actions
description: Transform raw meeting notes into organized summaries with action items and decisions
tags:
  - productivity
  - meetings
  - work
parameters:
  - name: output_style
    type: enum
    label: Output Style
    options:
      - Executive Summary
      - Detailed Minutes
      - Action Items Only
    default: Executive Summary
  - name: include_attendees
    type: boolean
    label: Extract Attendee List
    default: true
  - name: deadline_format
    type: enum
    label: Deadline Format
    options:
      - Relative (e.g., "by Friday")
      - Absolute (e.g., "by Jan 15")
      - Both
    default: Both
model:
  provider: openai
  name: gpt-4o
  temperature: 0.2
  max_tokens: 2000
preferred_clipboard_types:
  - text
---
Process these meeting notes and produce a structured summary.

**Output Style:** {{output_style}}
**Deadline Format:** {{deadline_format}}
{{#if include_attendees}}
Include a list of attendees mentioned in the notes.
{{/if}}

Please organize the output with these sections as applicable:
{{#if include_attendees}}
- **Attendees**: List of participants
{{/if}}
- **Summary**: Brief overview of the meeting
- **Key Decisions**: Decisions that were made
- **Action Items**: Tasks assigned with owners and deadlines
- **Open Questions**: Unresolved items needing follow-up

Today's date for reference: {{currentDate}}

---

**Meeting Notes:**

{{clipboard}}
