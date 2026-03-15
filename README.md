# English Coding Coach

A skill that helps Japanese developers build English skills naturally through everyday coding. The agent always responds in English with inline vocabulary support — no English lessons, just real coding assistance that happens to teach you English along the way.

This skill follows the open [Agent Skills](https://agentskills.io) standard.

## Who is this for?

- Japanese developers who want to get comfortable coding in English
- Developers who struggle with English documentation and technical writing
- Anyone who wants to improve their English naturally through daily development work

## Compatible Agents

- [Claude Code](https://claude.ai/code) (Plugin or manual install)
- [OpenAI Codex CLI](https://github.com/openai/codex) (via Skills CLI)
- [Cursor](https://cursor.com/) (via Skills CLI)
- Any agent supporting the [Agent Skills](https://agentskills.io) format

## Features

| Feature | Description |
|---|---|
| **Inline vocabulary annotations** | `difficult-word (simpler synonym / 日本語)` — difficult words get English synonym + Japanese translation |
| **Bold main verbs** | Main verbs are **bolded** to make sentence structure easier to read |
| **One sentence per line** | Each sentence gets its own line for easier reading |
| **`jp:` summary** | Brief Japanese summary of the response content at the end |

## Examples

### 1. Bug fix — Asking about the cause of a bug

**You**: この関数がnullを返すんだけど原因わかる？

**Claude Code**:

> The function **returns** null because the conditional check on line 12 **doesn't account for** (fails to handle / 考慮していない) empty arrays.
> When `items.length` **is** zero, the early return **triggers** before the main logic **executes**.
>
> ```typescript
> if (!items || items.length === 0) {
>   return null; // ← this is the cause
> }
> ```
>
> You should **replace** this with a fallback (default value / デフォルト値) that **returns** an empty result instead of null.
>
> ---
> jp: items が空配列のとき早期リターンで null を返している。空の結果を返すように修正すべき。

### 2. Code review — Asking for improvements

**You**: このAPIのエラーハンドリング、もっと良くできない？

**Claude Code**:

> The current error handling **catches** all exceptions with a generic (general-purpose / 汎用的な) catch block.
> This **obscures** (hides / 隠す) the root cause and **makes** debugging harder.
>
> I'd suggest we **distinguish** (separate / 区別する) between client errors and server errors:
>
> ```typescript
> try {
>   const response = await fetch(url);
>   if (!response.ok) {
>     throw new HttpError(response.status, response.statusText);
>   }
>   return await response.json();
> } catch (error) {
>   if (error instanceof HttpError) {
>     logger.warn(`Client error: ${error.status}`);
>   } else {
>     logger.error('Unexpected failure', error);
>   }
>   throw error;
> }
> ```
>
> This **provides** better observability (ability to monitor / 監視のしやすさ) and **helps** you pinpoint (identify exactly / 正確に特定する) issues in production.
>
> ---
> jp: 汎用catchを廃止し、クライアントエラーとサーバーエラーを分けてログ出力。本番でのデバッグが容易になる。

### 3. New feature — Asking about implementation approach

**You**: ページネーション実装したいんだけど、cursor方式とoffset方式どっちがいい？

**Claude Code**:

> It **depends** on your use case.
>
> **Offset-based** pagination **is** straightforward (simple / シンプル) to implement, but it **suffers from** (has problems with / 問題がある) data inconsistency when rows **are inserted** or **deleted** between requests.
>
> **Cursor-based** pagination **eliminates** (removes completely / 完全に解消する) that problem because each page **is anchored** to a specific record, not a numeric position.
>
> For your case — a feed with frequently (often / 頻繁に) updated content — cursor-based **is** the better fit.
> The trade-off (compromise / トレードオフ) is that users **can't jump** to an arbitrary (any chosen / 任意の) page number.
>
> ---
> jp: 更新頻度が高いフィードにはcursor方式が適切。offset方式はデータ追加削除時にずれが生じる。ただしページ番号ジャンプはできない。

## Installation

### Option 1: Plugin (recommended)

Add the marketplace and install:

```bash
# Add marketplace
/plugin marketplace add enumura1/english-coding-coach

# Install the plugin
/plugin install english-coding-coach
```

Then copy `CLAUDE.md` to your project root (if you already have one, merge the contents):

```bash
curl -o CLAUDE.md https://raw.githubusercontent.com/enumura1/english-coding-coach/main/CLAUDE.md
```

### Option 2: Skills CLI (works with Claude Code, Codex, Cursor, etc.)

```bash
npx skills add enumura1/english-coding-coach
```

Then copy `CLAUDE.md` to your project root:

```bash
curl -o CLAUDE.md https://raw.githubusercontent.com/enumura1/english-coding-coach/main/CLAUDE.md
```

### Option 3: Manual copy

1. Copy `CLAUDE.md` to your project root (if you already have one, merge the contents)
2. Copy `skills/english-coaching/` folder to your project's `.claude/skills/` directory

All options require `CLAUDE.md` in your project root. `CLAUDE.md` defines the output rules, `SKILL.md` provides vocabulary reference data.

## How it works

- You write in Japanese or English — either is fine
- Claude Code always responds in English with inline vocabulary support
- No setup, no commands — just start coding

## Design principles

- **Coding first** — English learning is a side effect, not the main purpose
- **No over-annotation** — annotations stay under ~10% of non-code text
- **Code stays clean** — no annotations inside code blocks
- **No escape hatch** — `jp:` summarizes content but doesn't translate everything, so you still engage with the English text

## Skill Structure

```
english-coding-coach/
├── .claude-plugin/
│   └── plugin.json              # Plugin manifest
├── skills/
│   └── english-coaching/
│       └── SKILL.md             # Vocabulary reference & verb bolding rules
├── CLAUDE.md                    # Output behavior rules
├── marketplace.json             # Self-hosted marketplace definition
├── LICENSE                      # MIT
└── README.md
```

## Requirements

- [Claude Code](https://claude.ai/code) or any compatible agent installed
- No additional dependencies

## License

MIT
