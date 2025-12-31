---
schema_version: 1
title: Deep Research Query Builder
description: Craft comprehensive research queries for AI assistants, search engines, or literature reviews
tags:
  - research
  - productivity
  - learning
parameters:
  - name: topic
    type: text
    label: Research Topic
    required: true
    multiline: true
  - name: depth
    type: enum
    label: Research Depth
    options:
      - Overview (broad understanding)
      - Intermediate (key concepts and debates)
      - Expert (cutting-edge, primary sources)
    default: Intermediate (key concepts and debates)
  - name: time_scope
    type: enum
    label: Time Scope
    options:
      - All time
      - Last 5 years
      - Last year
      - Last 6 months
    default: Last 5 years
  - name: output_type
    type: enum
    label: Query Type
    options:
      - AI Assistant Query
      - Academic Search Terms
      - Boolean Search Query
    default: AI Assistant Query
  - name: specific_questions
    type: text
    label: Specific Questions (optional)
    required: false
    multiline: true
model:
  provider: openai
  name: gpt-4o
  temperature: 0.5
  max_tokens: 2000
---
Help me construct a comprehensive research query on the following topic.

**Topic:** {{topic}}

**Research Depth:** {{depth}}
**Time Scope:** {{time_scope}}
**Output Type:** {{output_type}}

{{#if specific_questions}}
**Specific questions I want answered:**
{{specific_questions}}
{{/if}}

Please generate:

1. **Primary Query**: A well-structured {{output_type}} that will yield comprehensive results
2. **Sub-queries**: 3-5 related queries to explore different angles
3. **Key Terms**: Important terminology and synonyms to include
4. **Exclusion Terms**: Terms to exclude to filter noise
5. **Suggested Sources**: Types of sources most likely to have quality information on this topic

{{#if specific_questions}}
6. **Question Mapping**: Which sub-queries address which of my specific questions
{{/if}}
