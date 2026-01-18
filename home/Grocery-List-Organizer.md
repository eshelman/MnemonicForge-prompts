---
schema_version: 1
title: Grocery List Organizer
description: Transform a messy grocery list into an organized shopping list sorted by store section for efficient shopping
tags:
  - home
  - shopping
  - organization
  - productivity
parameters:
  - name: store_type
    type: enum
    label: Primary Store Type
    options:
      - Standard supermarket
      - Warehouse club (Costco, Sam's)
      - Natural/organic store
      - Budget store (Aldi, Lidl)
    default: Standard supermarket
  - name: output_format
    type: enum
    label: Output Format
    options:
      - By store section
      - By meal/recipe
      - Alphabetical within sections
    default: By store section
  - name: include_quantities
    type: boolean
    label: Estimate Quantities if Missing
    default: true
  - name: budget_notes
    type: boolean
    label: Include Budget-Saving Tips
    default: false
  - name: items
    type: text
    label: Items to Organize
    required: true
    multiline: true
model:
  provider: openai
  name: gpt-4o
  temperature: 0.2
  max_tokens: 1500
preferred_clipboard_types:
  - text
---
Organize this grocery list for efficient shopping.

**Store Type:** {{store_type}}
**Format:** {{output_format}}
{{#if include_quantities}}
Estimate reasonable quantities for any items without specified amounts.
{{/if}}
{{#if budget_notes}}
Include money-saving tips and alternatives where applicable.
{{/if}}

Please organize into these sections as applicable:
- **Produce** (fruits and vegetables)
- **Meat & Seafood**
- **Dairy & Eggs**
- **Bakery**
- **Frozen Foods**
- **Pantry/Dry Goods**
- **Canned & Jarred**
- **Beverages**
- **Snacks**
- **Household & Cleaning**
- **Personal Care**
- **Other**

Also flag any items that:
- Might be found in multiple sections
- Could be seasonal or hard to find
- Have common substitutes

---

**My grocery list:**

{{items}}
