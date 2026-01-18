---
schema_version: 1
title: Home Project Planner
description: Plan DIY home improvement projects with detailed steps, materials lists, and helpful tips
tags:
  - home
  - diy
  - improvement
  - planning
parameters:
  - name: skill_level
    type: enum
    label: DIY Skill Level
    options:
      - Beginner (first-time DIYer)
      - Intermediate (comfortable with basic tools)
      - Advanced (experienced with various projects)
    default: Intermediate (comfortable with basic tools)
  - name: project_scope
    type: enum
    label: Project Scope
    options:
      - Quick fix (under 2 hours)
      - Weekend project
      - Multi-day project
      - Major renovation
    default: Weekend project
  - name: budget_range
    type: enum
    label: Budget Range
    options:
      - Minimal (under $50)
      - Moderate ($50-200)
      - Significant ($200-500)
      - Major investment ($500+)
    default: Moderate ($50-200)
  - name: tool_availability
    type: enum
    label: Tool Availability
    options:
      - Basic hand tools only
      - Standard home toolkit
      - Well-equipped workshop
      - Will rent/buy as needed
    default: Standard home toolkit
  - name: project_description
    type: text
    label: Project Description
    required: true
    multiline: true
  - name: constraints
    type: text
    label: Constraints or Concerns (optional)
    required: false
    multiline: true
model:
  provider: openai
  name: gpt-4o
  temperature: 0.5
  max_tokens: 2500
---
Help me plan this home improvement project:

**Skill Level:** {{skill_level}}
**Project Scope:** {{project_scope}}
**Budget Range:** {{budget_range}}
**Tool Availability:** {{tool_availability}}

**Project Description:**
{{project_description}}

{{#if constraints}}
**Constraints/Concerns:**
{{constraints}}
{{/if}}

Please provide a comprehensive project plan including:

1. **Project Overview**:
   - Feasibility assessment for my skill level
   - Realistic budget estimate
   - Time estimate breakdown

2. **Materials List**:
   - Complete list with estimated quantities
   - Approximate costs for each item
   - Where to purchase (hardware store, specialty, online)
   - Alternative/budget options where applicable

3. **Tools Required**:
   - Essential tools (must have)
   - Nice-to-have tools (make job easier)
   - Rental recommendations if applicable

4. **Step-by-Step Instructions**:
   - Clear, numbered steps
   - Tips for each critical step
   - Common mistakes to avoid

5. **Safety Considerations**:
   - Required safety equipment
   - Potential hazards and precautions
   - When to stop and call a professional

6. **Pro Tips**:
   - Techniques for professional-looking results
   - Time-saving shortcuts
   - Quality checks along the way

7. **Cleanup & Finishing**:
   - Proper disposal of materials
   - Final touches for best results
