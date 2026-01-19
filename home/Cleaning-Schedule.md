---
schema_version: 1
title: Cleaning Schedule Generator
description: Create a personalized cleaning schedule with daily, weekly, and monthly tasks based on your home and lifestyle
tags:
  - home
  - cleaning
  - organization
  - productivity
parameters:
  - name: home_type
    type: enum
    label: Home Type
    options:
      - Studio/1-bedroom apartment
      - 2-3 bedroom apartment/house
      - 4+ bedroom house
      - Large home with multiple levels
    default: 2-3 bedroom apartment/house
  - name: household_members
    type: enum
    label: Household Members
    options:
      - Just me
      - 2 adults
      - Family with young children
      - Family with teens/adults
      - Roommates
    default: 2 adults
  - name: pets
    type: enum
    label: Pets
    options:
      - None
      - Cat(s)
      - Dog(s)
      - Multiple/other pets
    default: None
  - name: time_available
    type: enum
    label: Cleaning Time Available
    options:
      - Minimal (15-20 min/day)
      - Moderate (30-45 min/day)
      - Flexible (1+ hour available)
    default: Moderate (30-45 min/day)
  - name: schedule_style
    type: enum
    label: Schedule Style
    options:
      - Daily tasks spread throughout week
      - Concentrated weekend cleaning
      - Zone cleaning (one area per day)
    default: Daily tasks spread throughout week
  - name: special_areas
    type: text
    label: Special Areas/Concerns (optional)
    required: false
    multiline: true
model:
  provider: openai
  name: gpt-4o
  temperature: 0.4
  max_tokens: 2000
---
Create a comprehensive cleaning schedule with the following parameters:

**Home Type:** {{home_type}}
**Household:** {{household_members}}
**Pets:** {{pets}}
**Time Available:** {{time_available}}
**Schedule Style:** {{schedule_style}}

{{#if special_areas}}
**Special Areas/Concerns:**
{{special_areas}}
{{/if}}

Please provide:
1. **Daily Tasks**: Quick tasks to maintain cleanliness (5-10 minutes)
2. **Weekly Schedule**: Day-by-day breakdown of cleaning tasks
3. **Monthly Tasks**: Deep cleaning and maintenance tasks to rotate through
4. **Seasonal Tasks**: Quarterly or bi-annual cleaning projects
5. **Supplies Checklist**: Recommended cleaning supplies to have on hand
6. **Time-Saving Tips**: Efficiency suggestions based on the selected schedule style

Format the schedule as a clear, actionable checklist that's easy to follow.
