# English Coding Coach — Claude Code Skill

Claude Code のコーディング支援を英語で受けながら、自然に英語力を身につけるためのスキルです。

## Features

| Feature | Description |
|---|---|
| **Inline vocabulary annotations** | `difficult-word (simpler synonym / 日本語)` — difficult words get English synonym + Japanese translation |
| **Bold main verbs** | Main verbs are **bolded** to make SVO sentence structure visible |
| **One sentence per line** | Each sentence gets its own line for easier reading |
| **`jp:` summary** | Brief Japanese summary of the response content at the end |

## Sample Output

```
The component **re-renders** too often because the parent **passes** a new object reference on every render.
This **causes** unnecessary overhead (extra cost / 余分な負荷) for the child components.

To mitigate (reduce / 軽減する) this, we should **memoize** (cache the result of / 結果をキャッシュする) the expensive computation.
`useMemo` **prevents** redundant (unnecessary / 冗長な) recalculations when the dependencies **haven't changed**.

---
jp: 親コンポーネントが毎回新しいオブジェクト参照を渡すのが原因。useMemoでキャッシュして不要な再レンダリングを防止。
```

## Installation

1. Copy `CLAUDE.md` to your project root
2. Copy `.claude/skills/english-coaching/` folder to your project's `.claude/skills/` directory

```
your-project/
├── CLAUDE.md                              # Behavior rules
└── .claude/
    └── skills/
        └── english-coaching/
            └── SKILL.md                   # Vocabulary reference data
```

Both files are required. `CLAUDE.md` defines the output rules, `SKILL.md` provides vocabulary reference data.

## How it works

- You write in Japanese or English — either is fine
- Claude Code always responds in English with inline vocabulary support
- No setup, no commands — just start coding

## Design principles

- **Coding first** — English learning is a side effect, not the main purpose
- **No over-annotation** — annotations stay under ~10% of non-code text
- **Code stays clean** — no annotations inside code blocks
- **No escape hatch** — `jp:` summarizes content but doesn't translate everything, so you still engage with the English text
