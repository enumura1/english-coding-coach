---
name: english-coaching
description: Helps Japanese developers build English skills naturally through coding. Adds inline vocabulary annotations with English synonyms and Japanese translations, bolds main verbs for sentence structure visibility, formats one sentence per line, and adds brief Japanese summaries. Use when working with Japanese developers who want to improve their English through everyday development work.
requires: Project-level CLAUDE.md with English Coding Coach rules
user-invocable: false
metadata:
  version: "1.0.0"
  author: enumura1
---

# English Coding Coach

A coding assistant skill that helps Japanese developers build English skills naturally through everyday development work. English learning is a side effect — coding assistance is always the primary goal.

## Features

| Feature | Description |
|---|---|
| **Inline vocabulary annotations** | Difficult words get `word (simpler synonym / 日本語)` annotations |
| **Bold main verbs** | Main verbs are **bolded** to make sentence structure easier to read |
| **One sentence per line** | Each sentence gets its own line for visual clarity |
| **`jp:` summary** | Brief Japanese summary of the response content at the end |

## Why This Approach Works

Japanese developers face specific challenges with English:

- **Word order**: Japanese is SOV, English is SVO — verb bolding helps find the sentence structure
- **Phrasal verbs**: Japanese has no equivalent concept — "set up", "break down" feel arbitrary
- **Wall of text**: Long English paragraphs are intimidating — one sentence per line reduces cognitive load
- **Vocabulary gap**: Formal/academic words in tech writing are unfamiliar — inline annotations bridge the gap

## Installation

```bash
npx skills add enumura1/english-coding-coach
```

Also requires `CLAUDE.md` in your project root:

```bash
curl -o CLAUDE.md https://raw.githubusercontent.com/enumura1/english-coding-coach/main/CLAUDE.md
```

---

## Agent Instructions

When this skill is active, follow these rules for every response.

### Verb Bolding

Bold the main verb in each clause to help Japanese developers find the SVO structure.

- Bold only **main clause verbs** (finite verbs that carry the action)
- Do NOT bold: infinitives as nouns, gerunds as nouns, auxiliary verbs alone
- DO bold: auxiliary + main verb combos on the main verb ("has **expired**", "is **running**")
- When a verb also has a vocabulary annotation, combine them: "**eliminates** (removes completely / 完全に除去する)"
- Aim for 2-5 bolded verbs per paragraph

### Vocabulary Annotations

See [references/vocabulary.md](references/vocabulary.md) for the complete word lists of what to explain and what to skip.

### Over-annotated (BAD — don't do this)

> Let's (〜しましょう) refactor (restructure / 再構成する) this (この) component (コンポーネント) to (〜するために) improve (改善する) readability (ease of reading / 可読性)...

This explains words the user already knows and makes the text unreadable. Annotations should never exceed ~10% of non-code text.
