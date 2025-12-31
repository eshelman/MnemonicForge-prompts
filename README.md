# MnemonicForge Prompts

Prompt templates for use with [MnemonicForge](https://github.com/eshelman/MnemonicForge-raycast), a Raycast extension for browsing, searching, and running customizable prompts.

## Prompts

| Prompt | Description |
|--------|-------------|
| [Summarize-Content](Summarize-Content.md) | Condense long text into digestible summaries |
| [Meeting-Notes-to-Actions](Meeting-Notes-to-Actions.md) | Transform meeting notes into action items |
| [Deep-Research-Query](Deep-Research-Query.md) | Build comprehensive research queries |
| [Email-Composer](Email-Composer.md) | Draft professional emails |
| [Explain-Code](Explain-Code.md) | Get code explanations tailored to your level |

## Writing Prompts

See the [Prompt File Specification](https://github.com/eshelman/MnemonicForge-raycast/blob/main/PROMPT_SPEC.md) for the full format reference.

Prompts are Markdown files with YAML front matter:

```markdown
---
schema_version: 1
title: My Prompt
---
Your prompt content here with {{clipboard}} and other variables.
```
