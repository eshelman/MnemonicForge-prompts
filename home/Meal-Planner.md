---
schema_version: 1
title: Weekly Meal Planner
description: Generate a customized weekly meal plan based on dietary preferences, household size, and cooking time availability
tags:
  - home
  - cooking
  - planning
  - health
parameters:
  - name: household_size
    type: enum
    label: Household Size
    options:
      - 1 person
      - 2 people
      - 3-4 people
      - 5+ people
    default: 2 people
  - name: dietary_preference
    type: enum
    label: Dietary Preference
    options:
      - No restrictions
      - Vegetarian
      - Vegan
      - Low-carb/Keto
      - Gluten-free
      - Dairy-free
    default: No restrictions
  - name: cooking_time
    type: enum
    label: Weeknight Cooking Time
    options:
      - Quick (under 30 min)
      - Moderate (30-45 min)
      - Flexible (any duration)
    default: Moderate (30-45 min)
  - name: budget
    type: enum
    label: Budget Level
    options:
      - Budget-friendly
      - Moderate
      - No budget constraints
    default: Moderate
  - name: cuisine_preferences
    type: text
    label: Preferred Cuisines (optional)
    required: false
  - name: ingredients_to_use
    type: text
    label: Ingredients to Use Up (optional)
    required: false
    multiline: true
model:
  provider: openai
  name: gpt-4o
  temperature: 0.7
  max_tokens: 2000
---
Create a weekly meal plan (Monday-Sunday) with the following requirements:

**Household Size:** {{household_size}}
**Dietary Preference:** {{dietary_preference}}
**Weeknight Cooking Time:** {{cooking_time}}
**Budget Level:** {{budget}}

{{#if cuisine_preferences}}
**Preferred Cuisines:** {{cuisine_preferences}}
{{/if}}

{{#if ingredients_to_use}}
**Please incorporate these ingredients:**
{{ingredients_to_use}}
{{/if}}

Please provide:
1. **Weekly Overview**: A quick reference table of all meals
2. **Daily Breakdown**: For each day include:
   - Breakfast
   - Lunch
   - Dinner
   - Optional snack suggestion
3. **Meal Prep Tips**: Suggestions for preparing ingredients ahead of time
4. **Grocery Categories**: A consolidated list organized by store section (produce, proteins, dairy, pantry, etc.)
5. **Leftover Strategy**: How to repurpose leftovers to minimize waste
