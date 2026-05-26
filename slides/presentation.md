---
marp: true
theme: default
paginate: true
size: 16:9
header: 'AI Hands-on Workshop'
footer: 'Randy Vroegop — randy@vroegop.me'
style: |
  @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=Fraunces:opsz,wght@9..144,400;9..144,600;9..144,700&family=JetBrains+Mono:wght@400;500&display=swap');

  :root {
    --bg: #faf8f4;
    --ink: #1a1a1a;
    --muted: #6b6b6b;
    --accent: #c2410c;
    --code-bg: #f1ede5;
  }

  section {
    background: var(--bg);
    color: var(--ink);
    font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
    font-size: 24px;
    font-weight: 400;
    line-height: 1.45;
    padding: 60px 80px 70px;
    letter-spacing: -0.005em;
  }

  h1, h2, h3 {
    font-family: 'Fraunces', Georgia, serif;
    font-weight: 600;
    letter-spacing: -0.02em;
    line-height: 1.1;
    color: var(--ink);
  }

  h1 { font-size: 52px; margin: 0 0 0.3em; }
  h2 {
    font-size: 36px;
    margin: 0 0 0.5em;
    padding-bottom: 0.25em;
    border-bottom: 2px solid var(--accent);
    display: inline-block;
  }
  h3 { font-size: 26px; font-weight: 500; color: var(--muted); margin: 0 0 0.6em; }

  strong { font-weight: 600; color: var(--ink); }
  em { font-style: italic; }
  a { color: var(--accent); text-decoration: none; border-bottom: 1px solid currentColor; }

  ul, ol { padding-left: 1.2em; margin: 0.4em 0; }
  li { margin: 0.2em 0; }
  li::marker { color: var(--accent); }

  code {
    font-family: 'JetBrains Mono', ui-monospace, monospace;
    background: var(--code-bg);
    padding: 1px 6px;
    border-radius: 3px;
    font-size: 0.9em;
  }
  pre {
    font-family: 'JetBrains Mono', ui-monospace, monospace;
    background: var(--code-bg);
    border-left: 3px solid var(--accent);
    border-radius: 0;
    padding: 16px 20px;
    font-size: 18px;
    line-height: 1.5;
    margin: 0.6em 0;
  }
  pre code { background: transparent; padding: 0; }

  blockquote {
    border: none;
    border-left: 3px solid var(--accent);
    padding-left: 1em;
    margin: 0.6em 0 0;
    color: var(--muted);
    font-style: italic;
    font-family: 'Fraunces', Georgia, serif;
    font-size: 1.05em;
  }

  table { border-collapse: collapse; width: 100%; font-size: 0.95em; }
  th, td { text-align: left; padding: 8px 12px; border-bottom: 1px solid #d9d4ca; }
  th { border-bottom: 2px solid var(--accent); font-weight: 600; }

  header, footer {
    color: var(--muted);
    font-size: 13px;
    font-weight: 400;
    letter-spacing: 0.04em;
    text-transform: uppercase;
  }
  section::after { color: var(--muted); font-size: 13px; font-weight: 500; }

  /* SVG icons (outline, stroke = current accent) */
  svg.icon { stroke: var(--accent); fill: none; stroke-width: 1.5; stroke-linecap: round; stroke-linejoin: round; }
  svg.icon-xl { width: 140px; height: 140px; stroke-width: 1.25; }
  svg.icon-lg { width: 80px; height: 80px; }
  svg.icon-md { width: 44px; height: 44px; vertical-align: middle; margin-right: 0.4em; }
  svg.icon-sm { width: 28px; height: 28px; vertical-align: middle; margin-right: 0.3em; }

  /* Lead / section-divider slides */
  section.lead {
    background: var(--ink);
    color: var(--bg);
    padding: 90px 100px;
    display: flex;
    flex-direction: column;
    justify-content: center;
  }
  section.lead h1 { color: var(--bg); font-size: 80px; line-height: 1; }
  section.lead h2 { color: var(--bg); border: none; opacity: 0.85; font-weight: 400; font-style: italic; }
  section.lead h3 { color: var(--bg); opacity: 0.65; font-weight: 400; font-style: italic; }
  section.lead svg.icon { stroke: var(--accent); }
  section.lead strong { color: var(--accent); }
  section.lead blockquote { color: var(--bg); opacity: 0.8; border-left-color: var(--accent); }
  section.lead a { color: var(--accent); border-bottom-color: var(--accent); }
  section.lead::after { color: var(--bg); opacity: 0.4; }
  section.lead header, section.lead footer { color: var(--bg); opacity: 0.3; }

  /* Section-themed accent colors */
  section.part-concepts { --accent: #c2410c; }   /* burnt orange */
  section.part-demo     { --accent: #0f766e; }   /* deep teal */
  section.part-handson  { --accent: #6d28d9; }   /* violet */
  section.part-qa       { --accent: #b91c1c; }   /* deep red */
  section.part-tips     { --accent: #15803d; }   /* forest */

  /* Layout helpers */
  .columns { display: grid; grid-template-columns: 1fr 1fr; gap: 2.5rem; }
  .cols-3  { display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 1.8rem; }
  .small   { font-size: 19px; color: var(--muted); }
  .lede    { font-size: 28px; line-height: 1.35; color: var(--ink); margin: 0.2em 0 0.6em; }
  .kicker  { font-family: 'Inter', sans-serif; font-size: 14px; font-weight: 600; letter-spacing: 0.18em; text-transform: uppercase; color: var(--accent); margin-bottom: 1em; }
  .row     { display: flex; align-items: center; gap: 1rem; margin: 0.4em 0; }
  .center  { text-align: center; }
  .stack   { display: flex; flex-direction: column; gap: 0.4em; }

  /* Intro / bio slide */
  section.bio { padding: 70px 90px; }
  section.bio .bio-grid { display: grid; grid-template-columns: 1.4fr 1fr; gap: 3rem; align-items: center; }
  section.bio h1 { font-size: 64px; }
  section.bio .role { font-family: 'Fraunces', serif; font-size: 28px; font-style: italic; color: var(--muted); margin: 0.2em 0 1em; }
  section.bio ul { font-size: 22px; }
  section.bio .contact { margin-top: 1em; font-size: 20px; color: var(--muted); }
  section.bio .contact a { color: var(--accent); }
  section.bio .portrait { aspect-ratio: 1 / 1; border-radius: 8px; background: var(--ink); display: flex; align-items: center; justify-content: center; }
  section.bio .portrait svg { stroke: var(--accent); fill: none; stroke-width: 1; width: 60%; height: 60%; }
---

<!-- _class: bio part-concepts -->

<div class="bio-grid">
<div>

<div class="kicker">Workshop host</div>

# Randy Vroegop

<div class="role">Developer · AI-native engineering practice</div>

- TODO: current role / company
- TODO: years of experience, stack
- TODO: a one-line story about how you got into agentic workflows
- TODO: something personal (hobby, side project, where you live)

<div class="contact">

[randy@vroegop.me](mailto:randy@vroegop.me) · [linkedin.com/in/randy-vroegop](https://www.linkedin.com/in/randy-vroegop/)

</div>

</div>
<div class="portrait">

<svg viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg">
  <circle cx="50" cy="38" r="16"/>
  <path d="M20 86 C 24 64, 76 64, 80 86"/>
</svg>

</div>
</div>

---

<!-- _class: lead part-concepts -->

<svg class="icon icon-xl" viewBox="0 0 64 64" xmlns="http://www.w3.org/2000/svg">
  <path d="M14 30 L14 50 L50 50 L50 30"/>
  <path d="M8 30 L32 12 L56 30"/>
  <path d="M26 50 L26 38 L38 38 L38 50"/>
</svg>

# AI Hands-on for Developers

### From "AI fan" to AI-native engineer

One hour of concepts + demo, then you build.

---

<!-- _class: part-concepts -->

## What you'll leave with

- A mental model for **agents, subagents, MCP, and skills**
- A way to **structure documentation** that agents actually use
- Tools you can install today: **Grill-me-with-docs, GSD, OpenSpec, Superpowers, BTW**
- Hands-on exercises you can run on your own laptop
- Honest answers about the **risks** of working this way

---

<!-- _class: part-concepts -->

## Agenda

1. Concepts &nbsp;·&nbsp; <span class="small">≈25 min</span>
2. Live demo &nbsp;·&nbsp; <span class="small">≈25 min</span>
3. Hands-on walkthrough &nbsp;·&nbsp; <span class="small">do later</span>
4. Q&A &nbsp;·&nbsp; <span class="small">the questions that actually matter</span>
5. Tips from people who do this full-time

---

<!-- _class: lead part-concepts -->

<svg class="icon icon-xl" viewBox="0 0 64 64" xmlns="http://www.w3.org/2000/svg">
  <path d="M32 8 C 22 8, 16 16, 16 26 C 16 32, 18 36, 22 40 C 22 44, 20 48, 22 52 L 32 52"/>
  <path d="M32 8 C 42 8, 48 16, 48 26 C 48 32, 46 36, 42 40 C 42 44, 44 48, 42 52 L 32 52"/>
  <path d="M32 8 L 32 52"/>
  <circle cx="24" cy="22" r="1.5" fill="currentColor"/>
  <circle cx="40" cy="22" r="1.5" fill="currentColor"/>
</svg>

<div class="kicker">Part 1</div>

# Concepts

---

<!-- _class: part-concepts -->

## What is an agent markdown file?

An agent is mostly **a prompt + a tool list + a working directory**. The markdown file describes it.

```markdown
---
name: code-reviewer
description: Reviews diffs for correctness bugs.
tools: Read, Grep, Bash
model: sonnet
---

You are a senior reviewer. Focus on correctness, not style.
When you find a bug, cite file:line. Be terse.
```

---

<!-- _class: part-concepts -->

## Anatomy: frontmatter + body

<div class="columns">
<div>

**Frontmatter** — config
- `name` — stable identifier
- `description` — *when to use it*
- `tools` — least-privilege list
- `model` — match cost to task

</div>
<div>

**Body** — the prompt
- Role and scope
- Hard rules ("never do Z")
- Output format expectations
- Examples of good output

</div>
</div>

> `description` isn't human docs — it's how the router decides to delegate.

---

<!-- _class: part-concepts -->

## Setting up subagent documentation

Two failure modes:

1. **Too vague** — "helps with code". Router can't pick it.
2. **Too greedy** — claims everything. Gets called for tasks it can't do.

A good description answers:

- **Trigger** — what kind of request invokes me?
- **Scope** — what I will and won't do
- **Inputs / Outputs** — what context in, what shape out

---

<!-- _class: part-concepts -->

## When NOT to use a subagent

Subagents aren't free. Each one spawns a fresh context, costs briefing tokens, and hides what really happened.

**Skip subagents when:**

- The parent already has the context
- You need iterative, conversational work
- You need to *learn* from doing it
- You'd just be passing the same prompt through

> Delegate **searches and audits**, not **decisions**.

---

<!-- _class: part-concepts -->

## How agents use MCP servers

**MCP** = a standard way to expose tools to an agent. Filesystem, GitHub, Jira, Figma, your internal API.

```jsonc
// .claude/settings.json
{
  "mcpServers": {
    "github": { "command": "npx", "args": ["-y", "@modelcontextprotocol/server-github"] }
  }
}
```

The agent doesn't *know* GitHub — it knows there's a tool called `create_pull_request` it can call.

---

<!-- _class: part-concepts -->

## How agents use skills

A **skill** = a reusable, named playbook the agent loads on demand.

<div class="columns">
<div>

**Without skills**
- One giant system prompt
- All instructions always loaded
- Token bloat
- Conflicting advice

</div>
<div>

**With skills**
- Lean default context
- Loaded just in time
- Composable
- Easier to maintain

</div>
</div>

---

<!-- _class: part-concepts -->

## Teach the agent to build its own skills

When you repeat a workflow → make it a skill.

Prompt pattern:

> "I just did X three times. Extract it into a skill named `<name>`. Put it in `.claude/skills/`."

The agent will:

1. Summarize the repeated steps
2. Write frontmatter with a trigger description
3. Save the playbook — loaded automatically next session

---

<!-- _class: part-concepts -->

## Why documentation matters more, not less

Old world: docs are for humans who forget.
New world: docs are **the runtime context for your agent**.

- Agents can't read your mind, your Slack, or last week's meeting
- Their only ground truth is what's in the repo
- Bad docs → confident wrong answers (and you'll trust them)

> If it's not in the repo, the agent will invent it.

---

<!-- _class: part-concepts -->

## Structure: router + leaves

<div class="columns">
<div>

**Anti-pattern**

```
CLAUDE.md  (4,000 lines)
```

- Always loaded
- Burns tokens every turn
- Contradictions pile up
- Nobody updates it

</div>
<div>

**Pattern**

```
CLAUDE.md (router, ~100 lines)
docs/
  architecture.md
  testing.md
  domain/
    billing.md
```

</div>
</div>

---

<!-- _class: part-concepts -->

## What goes in the router

```markdown
# Project router

## Quick facts
- Stack: TypeScript, Postgres, Next.js
- Test: `npm test`   ·   Lint: `npm run lint`

## Where to look
- Architecture decisions → `docs/architecture.md`
- Testing conventions   → `docs/testing.md`
- Domain: billing       → `docs/domain/billing.md`

## House rules
- No `any` in TS
- Prefer composition over inheritance
```

Small, stable, **tells the agent where to read next**.

---

<!-- _class: part-concepts -->

## Why not one big file?

- Every token in always-loaded context is paid **every turn**
- Long context degrades reasoning ("lost in the middle")
- Agents skim — focused 200-line docs get read
- Humans can review small docs; nobody reviews 4,000-line ones
- Router docs survive refactors; monoliths rot

---

<!-- _class: part-concepts -->

## Tool tour: five to know

| Tool | What it does |
|---|---|
| **Grill-me-with-docs** | Forces the agent to *interview* you before writing code |
| **Get Shit Done (GSD)** | Opinionated workflow for shipping a task end-to-end |
| **OpenSpec** | Spec-first development; agent works from a spec doc |
| **Superpowers** | A curated bundle of high-quality skills |
| **BTW (`/btw`)** | Side-channel session info, no context poisoning |

---

<!-- _class: part-concepts -->

## Grill-me-with-docs

**Problem:** vague prompt → AI fills the gaps with assumptions → wrong code.

**Fix:** the skill makes the agent ask the questions a senior engineer would ask, *before* any code:

- "What's the failure mode you're worried about?"
- "Is this a hot path?"
- "Who else writes to this table?"

You write down what you actually want. The code follows from that.

---

<!-- _class: part-concepts -->

## Get Shit Done (GSD)

A workflow skill that drives a task to completion:

1. Restate the task
2. Identify files to touch
3. Make the change
4. Run tests
5. Self-review the diff
6. Commit with a real message

Opinionated. Predictable. Great for chores and small features.

---

<!-- _class: part-concepts -->

## OpenSpec

Spec-first. You write (or generate) a spec markdown, then the agent implements **against the spec, not the chat**.

- Spec is reviewable, diffable, version-controlled
- Stable target — chat drift doesn't change scope
- When the spec is wrong, you fix the spec, not the code

Great for: anything you'd put in a ticket.

---

<!-- _class: part-concepts -->

## Superpowers

A curated **skill pack**. Think "linter, but for AI workflows."

- Skills for verifying changes
- Skills for security review
- Skills for running the app
- Skills for refactoring chores

Install once, every project benefits.

---

<!-- _class: part-concepts -->

## BTW (`/btw`)

"By the way…" — surface session info **without** polluting the conversation context.

Use cases:

- "What model am I on?"
- "How much context have I used?"
- "What permissions are active?"

The answer is a side panel, not a message the next reply has to re-read.

---

<!-- _class: part-concepts -->

## Why too much context is bad

- **Cost** — every token paid every turn
- **Latency** — bigger prompt, slower response
- **Quality** — models reason worse on long contexts
- **Confusion** — stale info biases new answers
- **Hidden state** — you lose track of what the model "knows"

> Context is not a junk drawer. It's working memory.

---

<!-- _class: part-concepts -->

## Clear the context when…

- You're switching tasks
- The agent is stuck in a wrong assumption
- You're about to do something high-stakes
- The conversation is full of dead ends

> Re-establishing context is cheap; cleaning up after a confused agent is not.

---

<!-- _class: part-concepts -->

## Compact the context when…

- You want to keep the *conclusions* but drop the *exploration*
- You're mid-task and approaching limits
- Early turns are no longer relevant but the decisions still are

> Default: clear more often than you think.

---

<!-- _class: lead part-demo -->

<svg class="icon icon-xl" viewBox="0 0 64 64" xmlns="http://www.w3.org/2000/svg">
  <circle cx="32" cy="32" r="24"/>
  <path d="M26 22 L 44 32 L 26 42 Z"/>
</svg>

<div class="kicker">Part 2</div>

# Live demo

### I drive · you watch · questions welcome

---

<!-- _class: part-demo -->

## Demo plan

1. `/grill-me-with-docs` on a fake feature request
2. **GSD vs OpenSpec** on the same task — side by side
3. Tour of **Superpowers** skills
4. `/btw` mid-session to check state
5. A real `CLAUDE.md` router file
6. Doc structure with router + leaves
7. A real subagent markdown file

---

<!-- _class: part-demo -->

## Demo 1 — Grill me with docs

Prompt I'll use:

> "Add rate limiting to our public API."

Watch what the agent asks back **before** writing a line of code. Notice how the questions surface assumptions I hadn't made.

---

<!-- _class: part-demo -->

## Demo 2 — GSD vs OpenSpec

Same task: *"Add a `/health` endpoint that checks DB connectivity."*

- **GSD** — chat → implementation → tests → commit
- **OpenSpec** — write spec → review → implement → tests → commit

Compare: time to first commit, reviewability, what happens when I change my mind mid-task.

---

<!-- _class: part-demo -->

## Demo 3 — Superpowers tour

What installing Superpowers gives you:

- `verify` — actually run the app to confirm a change works
- `code-review` — review the current diff for bugs
- `security-review` — focused security pass
- `run` — launch the project the right way

We'll trigger `verify` on a real change.

---

<!-- _class: part-demo -->

## Demo 4 — `/btw`

Mid-demo, I'll run `/btw` and ask:

- What model am I on?
- What permissions are active?
- How much context is left?

Notice the answer **doesn't** show up as a message the next prompt has to ingest.

---

<!-- _class: part-demo -->

## Demo 5 — A real CLAUDE.md router

We'll open the project's `CLAUDE.md` and walk through:

- The "quick facts" block
- The routing table to deeper docs
- The "house rules" section
- What is **not** in this file (and why)

---

<!-- _class: part-demo -->

## Demo 6 — Docs with a router

```
CLAUDE.md
docs/
  architecture.md
  testing.md
  domain/
    billing.md
    auth.md
.claude/
  agents/
    code-reviewer.md
    migration-checker.md
  skills/
    deploy-check/SKILL.md
```

The router points; the leaves explain.

---

<!-- _class: part-demo -->

## Demo 7 — A subagent file

```markdown
---
name: migration-checker
description: Reviews SQL migrations for safety on large tables.
tools: Read, Grep, Bash
---

You review migrations against these rules:
- No NOT NULL on large tables without a backfill plan
- No CREATE INDEX without CONCURRENTLY
- No DROP COLUMN without a deprecation step

Report: safe / unsafe / needs-info, with file:line.
```

---

<!-- _class: lead part-handson -->

<svg class="icon icon-xl" viewBox="0 0 64 64" xmlns="http://www.w3.org/2000/svg">
  <path d="M40 12 L 52 24 L 44 32 L 38 26 L 22 42 L 22 48 L 16 48 L 16 42 L 32 26 L 26 20 Z"/>
  <circle cx="46" cy="18" r="2"/>
</svg>

<div class="kicker">Part 3</div>

# Hands-on

### Do this later — reproduce the demos on your own machine

---

<!-- _class: part-handson -->

## Setup (5 min)

```bash
# Clone a sandbox project (any small repo of yours works)
git clone <your-repo>
cd <your-repo>

# Install Claude Code
npm install -g @anthropic-ai/claude-code

# Initialize
claude init
```

You should now have a `.claude/` folder and a `CLAUDE.md`.

---

<!-- _class: part-handson -->

## Exercise 1 — Grill me with docs

1. Install the `grill-me-with-docs` skill
2. Prompt: *"Add a feature flag system to this project."*
3. Let the agent interview you
4. Save the answers as `docs/specs/feature-flags.md`
5. Then ask the agent to implement against that doc

> Goal: feel the difference between vibe coding and spec-driven prompts.

---

<!-- _class: part-handson -->

## Exercise 2 — GSD vs OpenSpec

Pick a real small task in your repo.

- Do it once with **GSD**
- Reset, do it again with **OpenSpec**

Compare the diffs and the time. Which one would you want for:

- a 30-minute chore?
- a 2-day feature?
- a risky refactor?

---

<!-- _class: part-handson -->

## Exercise 3 — Install Superpowers

1. Install the Superpowers skill pack
2. Make any small change in your repo
3. Run `/verify` — does it actually launch your app?
4. Run `/code-review` on the diff
5. Run `/security-review`

Notice what each skill is good at — and what it misses.

---

<!-- _class: part-handson -->

## Exercise 4 — `/btw` discipline

Use `/btw` at least three times during a session:

- Once to check your model
- Once to check context usage
- Once to ask "what files have I touched this session?"

> Train the muscle of asking **meta-questions out of band**.

---

<!-- _class: part-handson -->

## Exercise 5 — Write your CLAUDE.md router

Replace your `CLAUDE.md` with a router-style file:

- ≤100 lines
- Quick facts (stack, test cmd, lint cmd)
- Routing table to `docs/*`
- House rules

Then move detail into `docs/architecture.md`, `docs/testing.md`, etc.

> Bonus: ask the agent to do this *for* you.

---

<!-- _class: part-handson -->

## Exercise 6 — Router-style docs

Take your biggest existing doc (or your README) and split it:

- One **router** page (titles + one-line summary + link)
- N **leaf** pages, each focused

Re-run a typical prompt and compare: tokens used, quality of answer.

---

<!-- _class: part-handson -->

## Exercise 7 — Write a subagent

Create `.claude/agents/<your-agent>.md`:

```markdown
---
name: pr-describer
description: Writes PR descriptions from a diff.
tools: Bash, Read
---

You take the current git diff and produce:
- One-line title (<70 chars)
- Bulleted summary (3 bullets max)
- Test plan checklist
```

Use it on a real PR. Iterate until invocation feels reliable.

---

<!-- _class: lead part-qa -->

<svg class="icon icon-xl" viewBox="0 0 64 64" xmlns="http://www.w3.org/2000/svg">
  <circle cx="32" cy="32" r="24"/>
  <path d="M24 24 C 24 18, 30 16, 32 16 C 36 16, 40 18, 40 24 C 40 30, 32 30, 32 36"/>
  <circle cx="32" cy="44" r="2" fill="currentColor"/>
</svg>

<div class="kicker">Part 4</div>

# Q&A

### The questions that actually matter

---

<!-- _class: part-qa -->

## Do coding standards still matter?

**Short answer:** more than ever.

- The agent follows whatever pattern dominates the repo
- No standard → it averages across everything it's ever seen
- Standards are how you steer the agent without prompting every time

> Let the AI **execute** the standard. Don't let it **invent** it.

---

<!-- _class: part-qa -->

## Should we change architecture to suit AI?

A bit, yes — but not by inventing new patterns.

<div class="columns">
<div>

**Helps both AI & humans**
- Small modules, clear boundaries
- Pure functions where possible
- Explicit dependency injection
- Boring, predictable file layout

</div>
<div>

**Hurts AI**
- Magic, reflection, dynamic dispatch
- Implicit conventions
- Mega-files of mixed concerns

</div>
</div>

---

<!-- _class: part-qa -->

## Is testing strategy shifting?

Yes. Two real changes:

1. **More tests, lower cost.** Generating tests is cheap; running them is the new bottleneck.
2. **Tests as specs.** Tests become the contract the agent implements against.

> The agent is great at writing the tests *you* tell it to write. Mediocre at deciding *which* tests matter.

---

<!-- _class: part-qa -->

## Sharing AI assets — what to commit

**Commit to the repo:**

- `CLAUDE.md` router
- `docs/*` (leaf docs)
- `.claude/agents/*` (project subagents)
- `.claude/skills/*` (project skills)
- MCP server *configuration* (not secrets)

**Do NOT commit:** API keys, tokens, personal prefs, local paths, anything in `.claude/settings.local.json`.

---

<!-- _class: part-qa -->

## Sharing patterns

<div class="cols-3">
<div>

**Per-project**
- Lives in the repo
- Versioned with code
- Reviewed in PRs

</div>
<div>

**Per-person**
- `~/.claude/` for your own
- Personal subagents
- Keybindings, themes

</div>
<div>

**Per-org**
- Starter-pack repo
- Internal MCP server
- Shared conventions doc

</div>
</div>

---

<!-- _class: part-qa -->

## How I share knowledge

- Pair sessions, recorded
- A `docs/learnings/` folder — short, dated notes
- A team channel for "I figured out X today"
- Twice → it becomes a skill, committed
- Three times → it becomes a subagent

> Tacit knowledge dies. Committed markdown survives team turnover.

---

<!-- _class: part-qa -->

## How companies usually share (the messy truth)

- Confluence pages nobody reads
- A Slack channel of links nobody bookmarks
- "Ask Bob, he knows"
- Tribal knowledge that walks out with Bob

Agentic workflows make this **worse if you don't fix it** — the agent reads the repo, not Confluence.

> Repo-resident docs are the only kind that survive.

---

<!-- _class: lead part-qa -->

<svg class="icon icon-xl" viewBox="0 0 64 64" xmlns="http://www.w3.org/2000/svg">
  <path d="M32 8 L 52 18 L 52 32 C 52 44, 42 52, 32 56 C 22 52, 12 44, 12 32 L 12 18 Z"/>
  <path d="M24 32 L 30 38 L 42 26"/>
</svg>

<div class="kicker">Q&A continued</div>

# The risks

### Six honest ones — and how to protect yourself

---

<!-- _class: part-qa -->

## Risk 1 — Feeling fast, shipping less

You feel productive. You ship less.

- Time-to-PR is shorter
- Time-to-merged-and-stable is often **longer**
- Rework, debugging, re-prompting eats the gains

**Counter:** measure cycle time, track rework rate, treat "looks done" as suspicious until verified.

---

<!-- _class: part-qa -->

## Risk 2 — Knowing architecture, not code

You stop reading diffs carefully. You drift into being a manager of code.

Fine for some tasks. Dangerous for others.

**Counter:**

- Read every line for security-, money-, or data-touching code
- Periodically write code from scratch
- Demand the agent explain *why*, not just *what*

---

<!-- _class: part-qa -->

## Risk 3 — Hallucinations as features

The worst bugs: code that runs, passes tests, and is confidently wrong.

- Made-up API calls that happen to exist
- Plausible-looking math that's subtly off
- "Helpful" extra behavior nobody asked for

**Counter:** spec-first, property-based tests for risky logic, ask *"what did you change beyond what I asked?"*

---

<!-- _class: part-qa -->

## Risk 4 — Security gaps

Agents will happily:

- Disable a CSP header to fix a console error
- `chmod 777` to fix permissions
- Skip a hook with `--no-verify`
- Hardcode a "just for testing" secret

**Counter:** `/security-review` on every diff touching auth/headers/secrets. Pre-commit hooks the agent **cannot** bypass.

---

<!-- _class: part-qa -->

## Risk 5 — Large blast radius

"Refactor this function" → 47 files changed.

**Counter:**

- Constrain scope explicitly in the prompt
- `git diff --stat` before accepting
- A skill that rejects diffs touching > N files without confirmation

---

<!-- _class: part-qa -->

## Risk 6 — Bad structure costs real money

Every prompt loads context. Bad structure → bigger context → more tokens → more $.

- Monolithic files force loading the whole thing
- Implicit deps force exploratory grep
- Inconsistent naming forces retries

**Counter:** small files · explicit imports · consistent naming · router docs.

---

<!-- _class: part-qa -->

## Protecting yourself — the short list

1. **Spec before code** for anything non-trivial
2. **Verify** with the actual app, not just tests
3. **Read diffs** for anything security- or data-critical
4. **Constrain scope** in the prompt
5. **Commit your skills and agents** so the team benefits
6. **Measure cycle time**, not commits

---

<!-- _class: part-qa -->

## Debugging while pairing with AI

<div class="columns">
<div>

**Prompt-only**
- Fastest for shallow bugs
- Risky: agent guesses
- Good for: "error X on line Y"

</div>
<div>

**Pairing (REPL)**
- You drive hypotheses
- AI runs the experiments
- Good for: unfamiliar code

</div>
</div>

**Test-driven debug** — write the failing test first, let AI fix until green. Best for regressions.

---

<!-- _class: part-qa -->

## Is your own code easier to debug?

Yes — but the gap is closing.

- **Your code:** you remember the *why*, the trade-offs
- **AI code:** the agent remembers nothing; you read it cold

**Mitigations:**

- Have the agent leave **decision notes** in the PR description
- Force the agent to write the *failing test first*
- Keep diffs small enough to actually read

---

<!-- _class: lead part-tips -->

<svg class="icon icon-xl" viewBox="0 0 64 64" xmlns="http://www.w3.org/2000/svg">
  <path d="M16 10 L 16 56 L 32 46 L 48 56 L 48 10 Z"/>
</svg>

<div class="kicker">Part 5</div>

# Tips from the pros

### Links to read after the workshop

---

<!-- _class: part-tips -->

## Anthropic — building with Claude

- [Claude Code docs](https://code.claude.com/docs)
- [Engineering blog](https://www.anthropic.com/engineering)
- [Prompt engineering guide](https://docs.claude.com/en/docs/build-with-claude/prompt-engineering/overview)
- [Building effective agents](https://www.anthropic.com/engineering/building-effective-agents)

> Start here for primary-source guidance.

---

<!-- _class: part-tips -->

## Simon Willison — daily field notes

- [Blog](https://simonwillison.net/)
- [Things I've learned about LLMs](https://simonwillison.net/tags/llms/)

> He tries everything, writes it down the same day, and is honest about what didn't work.

---

<!-- _class: part-tips -->

## Andrej Karpathy — deep intuition

- [Intro to LLMs (YouTube)](https://www.youtube.com/watch?v=zjkBMFhNj_g)
- [Let's build GPT (YouTube)](https://www.youtube.com/watch?v=kCc8FmEb1nY)
- Twitter/X: **@karpathy**

> Understand *why* models behave the way they do, not just how to prompt them.

---

<!-- _class: part-tips -->

## Podcasts & long-form

- **Latent Space** — [latent.space](https://www.latent.space/)
- **Geoffrey Huntley** — [ghuntley.com](https://ghuntley.com/) (agentic workflows, real cases)

> Hear how real teams structure their workflows, what failed, what stuck.

---

<!-- _class: part-tips -->

## Following news without drowning

- **Hacker News** — Show HN / Ask HN threads
- **r/LocalLLaMA** for local/open-weight tooling
- **Anthropic + OpenAI + DeepMind** blogs only — skip the rest

> The signal-to-noise ratio is brutal. Curate hard.

---

<!-- _class: part-tips -->

## My one-page distilled advice

1. **Docs are runtime.** Router + leaves. Commit them.
2. **Spec before code** for anything that matters.
3. **Skills compound.** Repeated → skill → subagent → committed.
4. **Read the diff** — especially auth, money, data.
5. **Clear context often.**
6. **Measure cycle time**, not commits.
7. **Steal patterns from Anthropic, Simon Willison, Karpathy.**

---

<!-- _class: lead part-concepts -->

<svg class="icon icon-xl" viewBox="0 0 64 64" xmlns="http://www.w3.org/2000/svg">
  <path d="M12 20 L 32 36 L 52 20"/>
  <rect x="12" y="14" width="40" height="32" rx="2"/>
</svg>

# Thank you

### Questions?

[randy@vroegop.me](mailto:randy@vroegop.me) · [linkedin.com/in/randy-vroegop](https://www.linkedin.com/in/randy-vroegop/)

Slides, hands-on exercises and skill files live in this repo.
