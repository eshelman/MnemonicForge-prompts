---
schema_version: 1
title: Email Composer
description: Draft professional emails with customizable tone, structure, and purpose
tags:
  - productivity
  - communication
  - work
parameters:
  - name: purpose
    type: enum
    label: Email Purpose
    options:
      - Request/Ask
      - Follow-up
      - Thank You
      - Introduction
      - Update/Status
      - Decline/Apologize
    default: Request/Ask
  - name: tone
    type: enum
    label: Tone
    options:
      - Formal
      - Professional
      - Friendly Professional
      - Casual
    default: Professional
  - name: recipient_type
    type: enum
    label: Recipient
    options:
      - Executive/Senior Leader
      - Manager/Supervisor
      - Colleague/Peer
      - Client/Customer
      - External Contact
    default: Colleague/Peer
  - name: key_points
    type: text
    label: Key Points to Include
    required: true
    multiline: true
  - name: context
    type: text
    label: Additional Context (optional)
    required: false
    multiline: true
  - name: length
    type: enum
    label: Email Length
    options:
      - Brief (2-3 sentences)
      - Standard (1-2 paragraphs)
      - Detailed (3+ paragraphs)
    default: Standard (1-2 paragraphs)
model:
  provider: openai
  name: gpt-4o
  temperature: 0.4
  max_tokens: 1000
---
Draft an email with the following parameters:

**Purpose:** {{purpose}}
**Tone:** {{tone}}
**Recipient Type:** {{recipient_type}}
**Length:** {{length}}

**Key Points to Cover:**
{{key_points}}

{{#if context}}
**Additional Context:**
{{context}}
{{/if}}

Please provide:
1. A suggested subject line
2. The email body
3. A brief note on any adjustments I might consider based on my specific situation
