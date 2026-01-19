---
schema_version: 1
title: Home Maintenance Tracker
description: Generate a seasonal home maintenance checklist and schedule to keep your home in top condition
tags:
  - home
  - maintenance
  - planning
  - seasonal
parameters:
  - name: home_type
    type: enum
    label: Home Type
    options:
      - Apartment/Condo
      - Townhouse
      - Single-family home
      - Older home (pre-1980)
    default: Single-family home
  - name: climate
    type: enum
    label: Climate Zone
    options:
      - Cold winters, mild summers
      - Hot summers, mild winters
      - Four distinct seasons
      - Tropical/humid year-round
      - Dry/arid climate
    default: Four distinct seasons
  - name: current_season
    type: enum
    label: Current/Upcoming Season
    options:
      - Spring
      - Summer
      - Fall
      - Winter
    default: Spring
  - name: ownership
    type: enum
    label: Ownership Status
    options:
      - Owner (responsible for all maintenance)
      - Renter (limited maintenance responsibility)
      - HOA community (shared maintenance)
    default: Owner (responsible for all maintenance)
  - name: special_features
    type: text
    label: Special Features (pool, fireplace, etc.)
    required: false
    multiline: true
model:
  provider: openai
  name: gpt-4o
  temperature: 0.3
  max_tokens: 2500
---
Create a home maintenance checklist and schedule with these parameters:

**Home Type:** {{home_type}}
**Climate:** {{climate}}
**Current/Upcoming Season:** {{current_season}}
**Ownership:** {{ownership}}

{{#if special_features}}
**Special Features to Maintain:**
{{special_features}}
{{/if}}

**Current Date:** {{currentDate}}

Please provide:

1. **Immediate Tasks** (this month):
   - Priority maintenance items for the current season
   - Any time-sensitive inspections or preparations

2. **Seasonal Checklist** for {{current_season}}:
   - Interior tasks
   - Exterior tasks
   - Systems to inspect (HVAC, plumbing, electrical)
   - Safety checks (smoke detectors, CO detectors, etc.)

3. **Monthly Recurring Tasks**:
   - Quick maintenance items to do every month

4. **Annual Maintenance Calendar**:
   - Overview of what to do each season
   - Professional service reminders (HVAC tune-up, etc.)

5. **Warning Signs to Watch For**:
   - Issues that indicate needed repairs
   - When to call a professional vs. DIY

Format as actionable checklists with estimated time and difficulty for each task.
