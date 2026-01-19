---
schema_version: 1
title: Coloring Page Generator
description: Generate custom coloring page ideas and descriptions for both children and adults with adjustable complexity and themes
tags:
  - home
  - creative
  - family
  - art
parameters:
  - name: audience
    type: enum
    label: Target Audience
    options:
      - Young children (ages 3-5)
      - Kids (ages 6-10)
      - Tweens (ages 11-13)
      - Adults (relaxation/mindfulness)
      - All ages (family activity)
    default: Kids (ages 6-10)
  - name: complexity
    type: enum
    label: Design Complexity
    options:
      - Simple (large shapes, few details)
      - Moderate (medium detail, some patterns)
      - Intricate (fine details, patterns)
      - Highly detailed (mandalas, zentangle-style)
    default: Moderate (medium detail, some patterns)
  - name: theme
    type: enum
    label: Theme
    options:
      - Animals & Nature
      - Fantasy & Fairy Tales
      - Space & Science
      - Vehicles & Machines
      - Seasonal/Holiday
      - Patterns & Mandalas
      - Inspirational/Quotes
      - Food & Treats
    default: Animals & Nature
  - name: style
    type: enum
    label: Art Style
    options:
      - Cartoon/Whimsical
      - Realistic
      - Geometric/Abstract
      - Kawaii/Cute
      - Folk art/Decorative
    default: Cartoon/Whimsical
  - name: page_count
    type: enum
    label: Number of Designs
    options:
      - Single page
      - 3-page set
      - 5-page collection
      - 10-page activity book
    default: 3-page set
  - name: specific_requests
    type: text
    label: Specific Elements or Requests (optional)
    required: false
    multiline: true
  - name: include_activity
    type: boolean
    label: Include Activity Elements
    default: false
model:
  provider: openai
  name: gpt-4o
  temperature: 0.8
  max_tokens: 2000
---
Create coloring page concept(s) with the following specifications:

**Target Audience:** {{audience}}
**Complexity Level:** {{complexity}}
**Theme:** {{theme}}
**Art Style:** {{style}}
**Number of Designs:** {{page_count}}
{{#if include_activity}}
**Include:** Activity elements (hidden objects, mazes, connect-the-dots, or simple puzzles)
{{/if}}

{{#if specific_requests}}
**Special Requests:**
{{specific_requests}}
{{/if}}

For each coloring page design, please provide:

1. **Title**: A fun, descriptive name for the page

2. **Scene Description**: Detailed description of the image composition including:
   - Main subject(s) and their positioning
   - Background elements
   - Decorative details appropriate for the complexity level
   - Suggested focal points

3. **Design Elements**:
   - Key shapes and patterns to include
   - Areas with fine detail vs. larger sections (for variety)
   - Border or frame suggestions if applicable

4. **Age-Appropriate Considerations**:
{{#if (eq audience "Young children (ages 3-5)")}}
   - Extra-thick outlines for easy coloring
   - Large, distinct shapes
   - Friendly, non-scary imagery
{{/if}}
{{#if (eq audience "Adults (relaxation/mindfulness)")}}
   - Intricate patterns for meditative coloring
   - Sophisticated composition
   - Stress-relief focused design elements
{{/if}}

5. **Color Suggestions** (optional guide):
   - Recommended color palette
   - Areas that could use gradient techniques
   - Suggested media (crayons, colored pencils, markers)

{{#if include_activity}}
6. **Activity Elements**:
   - Type of activity integrated into the design
   - Instructions for completing the activity
   - How it connects to the coloring theme
{{/if}}

7. **Image Generation Prompt**: A ready-to-use prompt for AI image generators (like DALL-E or Midjourney) to create this as a black-and-white line art coloring page.

Make the designs engaging and fun to color while maintaining appropriate complexity for the selected audience.
