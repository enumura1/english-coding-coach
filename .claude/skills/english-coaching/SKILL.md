---
name: english-coaching
description: Background knowledge for English vocabulary coaching for Japanese developers. This skill provides word difficulty classification and Japanese developer context to guide inline vocabulary explanations.
user-invocable: false
---

# English Coaching — Vocabulary Reference

## Word Difficulty Classification

### Formal / Academic (always explain)
ubiquitous, albeit, inherently, mitigate, alleviate, convoluted, superfluous, extraneous, cumbersome, verbose, concise, ephemeral, immutable, idempotent, orthogonal, pragmatic, succinct, redundant, proliferate, circumvent, facilitate, expedite, encompass, augment, diminish, exacerbate

### Technical but Not Code (always explain)
bottleneck, overhead, trade-off, throughput, latency, caveat, workaround, gotcha, blocker, regression, flaky, deterministic, heuristic, payload, granularity, scalability, resilience, observability

### Idiomatic Expressions (always explain)
- out of the box → works immediately without configuration
- boilerplate → standard template code
- bikeshedding → debating trivial details
- yak shaving → doing seemingly unrelated tasks to accomplish the real task
- rubber ducking → explaining code to find bugs
- dogfooding → using your own product
- silver bullet → a perfect solution (that usually doesn't exist)
- tech debt → shortcuts that need fixing later
- happy path → the expected normal flow
- edge case → unusual situation at the boundary

### Phrasal Verbs (often confusing for Japanese speakers)
- set up (configure / 設定する)
- break down (divide into parts / 分解する)
- roll back (revert / 元に戻す)
- spin up (start / 起動する)
- tear down (remove / 削除する)
- figure out (understand / 理解する)
- come up with (think of / 思いつく)
- run into (encounter / 遭遇する)
- look into (investigate / 調べる)
- end up (eventually become / 結局〜になる)

### Programming Terms (NEVER explain)
function, variable, class, object, array, string, integer, boolean, float, loop, for, while, if, else, switch, case, return, import, export, module, component, props, state, hook, callback, promise, async, await, API, REST, HTTP, JSON, SQL, CLI, IDE, CI/CD, Git, Docker, npm, yarn, pip, cargo

### Katakana-Borrowed Words (NEVER explain)
error, file, server, client, code, test, bug, cache, debug, install, update, delete, comment, method, library, framework, template, deploy, merge, branch, commit, push, pull, browser, database, process, thread, container, image, log, config, build, compile, render, route, request, response

## Japanese Developer Context

### Common Struggles
- **Phrasal verbs**: Japanese has no equivalent concept. "Set up", "break down", "roll back" feel arbitrary.
- **Passive voice**: Overused in English technical writing. Japanese devs find it harder to parse than active voice.
- **Long subordinate clauses**: Nested "which/that/where" clauses are difficult. Prefer shorter sentences.
- **Articles (a/the)**: Japanese has no articles. Don't over-explain, but model correct usage.

### What Helps
- Clear subject-verb-object structure
- Explicit connectors: however, therefore, because, for example, in other words
- Numbered lists and bullet points for complex explanations
- Concrete examples over abstract descriptions

## Verb Bolding

Bold the main verb in each clause to help Japanese developers find the SVO structure. Japanese is SOV — the verb position is the biggest structural gap.

### Rules
- Bold only **main clause verbs** (finite verbs that carry the action)
- Do NOT bold: infinitives used as nouns ("to run is fun"), gerunds used as nouns ("running is fun"), auxiliary verbs alone ("is", "has" when used as helpers)
- DO bold: auxiliary + main verb combos on the main verb ("has **expired**", "is **running**")
- When a verb also has a vocabulary annotation, combine them: "**eliminates** (removes completely / 完全に除去する)"
- Aim for 2-5 bolded verbs per paragraph — not every single verb

### Good example
> The request **fails** because the authentication token **has expired** (is no longer valid / 有効期限切れ). The server **rejects** (refuses / 拒否する) the request with a 401 status code.

### Over-annotated (BAD — don't do this)
> Let's (〜しましょう) refactor (restructure / 再構成する) this (この) component (コンポーネント) to (〜するために) improve (改善する) readability (ease of reading / 可読性)...

The second example explains words the user already knows and makes the text unreadable.
