---
marp: true
theme: default
paginate: true
size: 16:9
header: 'AI Hands-on Workshop'
footer: '© 2026 — rjp.vroegop@gmail.com'
style: |
  @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=Fraunces:opsz,wght@9..144,400;9..144,600;9..144,700&family=JetBrains+Mono:wght@400;500&display=swap');

  :root {
    --bg: #faf8f4;
    --ink: #1a1a1a;
    --muted: #6b6b6b;
    --accent: #c2410c;
    --rule: #1a1a1a;
    --code-bg: #f1ede5;
  }

  section {
    background: var(--bg);
    color: var(--ink);
    font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
    font-size: 26px;
    font-weight: 400;
    line-height: 1.45;
    padding: 70px 80px;
    letter-spacing: -0.005em;
  }

  h1, h2, h3 {
    font-family: 'Fraunces', Georgia, serif;
    font-weight: 600;
    letter-spacing: -0.02em;
    line-height: 1.1;
    color: var(--ink);
  }

  h1 {
    font-size: 52px;
    margin-bottom: 0.3em;
  }
  h2 {
    font-size: 40px;
    margin-bottom: 0.5em;
    padding-bottom: 0.25em;
    border-bottom: 1px solid var(--ink);
  }
  h3 {
    font-size: 28px;
    font-weight: 500;
    color: var(--muted);
  }

  strong { font-weight: 600; color: var(--ink); }
  em { font-style: italic; }

  a { color: var(--accent); text-decoration: none; border-bottom: 1px solid currentColor; }

  ul, ol { padding-left: 1.2em; }
  li { margin: 0.25em 0; }
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
    padding: 18px 22px;
    font-size: 19px;
    line-height: 1.5;
  }
  pre code { background: transparent; padding: 0; }

  blockquote {
    border: none;
    border-left: 3px solid var(--accent);
    padding-left: 1em;
    margin-left: 0;
    color: var(--muted);
    font-style: italic;
    font-family: 'Fraunces', Georgia, serif;
    font-size: 1.05em;
  }

  table {
    border-collapse: collapse;
    width: 100%;
    font-size: 0.95em;
  }
  th, td {
    text-align: left;
    padding: 10px 14px;
    border-bottom: 1px solid #d9d4ca;
  }
  th {
    border-bottom: 2px solid var(--ink);
    font-weight: 600;
  }

  header, footer {
    color: var(--muted);
    font-size: 14px;
    font-weight: 400;
    letter-spacing: 0.04em;
    text-transform: uppercase;
  }
  section::after {
    color: var(--muted);
    font-size: 14px;
    font-weight: 500;
  }

  /* Lead / title slides */
  section.lead {
    text-align: left;
    padding: 90px 100px;
    background: var(--ink);
    color: var(--bg);
  }
  section.lead h1 {
    font-size: 88px;
    color: var(--bg);
    line-height: 1;
  }
  section.lead h2 {
    border: none;
    color: var(--bg);
    opacity: 0.7;
    font-weight: 400;
    font-style: italic;
  }
  section.lead h3 {
    color: var(--bg);
    opacity: 0.7;
    font-weight: 400;
    font-style: italic;
    margin-bottom: 2em;
  }
  section.lead strong { color: var(--accent); }
  section.lead::after { color: var(--bg); opacity: 0.5; }
  section.lead header, section.lead footer { color: var(--bg); opacity: 0.4; }
  section.lead blockquote { color: var(--bg); opacity: 0.8; }

  /* Layout helpers */
  .columns {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 2.5rem;
  }
  .small { font-size: 20px; color: var(--muted); }
---

<!-- _class: lead -->

# AI Hands-on for Developers

### From "AI fan" to AI-native engineer

One hour of concepts + demo, then you build.

---

## What you'll leave with

- A mental model for **agents, subagents, MCP, and skills**
- A way to **structure documentation** that agents actually use
- Tools you can install today: **Grill-me-with-docs, GSD, OpenSpec, Superpowers, BTW**
- Hands-on exercises you can run on your own laptop
- Honest answers about the **risks** of working this way

---

## Agenda

1. Concepts (≈25 min)
2. Live demo (≈25 min)
3. Hands-on you'll do later (walkthrough)
4. Q&A — the questions that actually matter
5. Tips from the people who do this full-time

---

<!-- _class: lead -->

# Part 1 — Concepts

---

## What is an "agent markdown file"?

An agent is mostly **a prompt + a tool list + a working directory**. The markdown file is how you describe it.

Typical structure:

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

- **Frontmatter** = machine-readable config (name, tools, model)
- **Body** = the system prompt the agent runs with

---

## Anatomy of a good agent file

<div class="columns">

**Frontmatter**
- `name` — stable identifier
- `description` — *when to use it*, written for the router
- `tools` — least-privilege list
- `model` — match cost to task

**Body**
- Role and scope ("you do X, not Y")
- Hard rules ("never do Z")
- Output format expectations
- Examples of good/bad output

</div>

> The `description` is not documentation for humans — it's how the main agent decides whether to delegate. Write it like a router rule.

---

## Setting up subagent documentation

Two failure modes:

1. **Too vague** — "helps with code". The router can't tell when to pick it.
2. **Too greedy** — claims everything. It gets called for tasks it can't do.

A good subagent description answers:

- **Trigger**: what kind of request invokes me?
- **Scope**: what I will/won't do
- **Inputs**: what context do I need handed in?
- **Output**: what does my reply look like?

---

## When NOT to use specialised subagents

Subagents are not free. Each one:

- Spawns a fresh context (no memory of the parent conversation)
- Costs extra tokens to brief
- Adds latency
- Can return summaries that hide what really happened

**Skip subagents when:**
- The task is short and the parent already has the context
- You need iterative, conversational work
- You need to *learn* from doing it (subagent learns, you don't)
- You'd just be passing the same prompt through

> Rule of thumb: delegate **searches and audits**, not **decisions**.

---

## How agents use MCP servers

**MCP (Model Context Protocol)** = a standard way to expose tools to an agent.

- Filesystem, GitHub, Jira, Figma, Slack, Postgres, your internal API…
- The agent sees them as tool calls; the MCP server does the work
- You configure them once, every agent in the project can use them

```jsonc
// .claude/settings.json
{
  "mcpServers": {
    "github": { "command": "npx", "args": ["-y", "@modelcontextprotocol/server-github"] }
  }
}
```

The agent doesn't "know" GitHub — it knows there's a tool called `create_pull_request` it can call.

---

## How agents use skills

A **skill** is a reusable, named playbook the agent can load on demand.

- Lives as a markdown file with a description + steps
- The agent picks it when the description matches the task
- Keeps the system prompt small until you need the skill

<div class="columns">

**Without skills**
- One giant system prompt
- All instructions always loaded
- Token bloat
- Conflicting advice

**With skills**
- Lean default context
- Specialized knowledge loaded just in time
- Composable
- Easier to maintain

</div>

---

## Teaching the agent to build its own skills

When you find yourself repeating a workflow → make it a skill.

Prompt pattern:

> "I just did X three times. Extract the steps into a skill named `<name>` with a description of when to use it. Put it in `.claude/skills/`."

The agent will:
1. Summarize the repeated steps
2. Write a frontmatter with a trigger description
3. Save the playbook

Next session: it loads the skill automatically when the trigger matches.

---

## Why documentation matters (more, not less)

Old world: docs are for humans who forget.
New world: docs are **the runtime context for your agent**.

- Agents can't read your mind, your Slack, or last week's meeting
- Their only ground truth is what's in the repo
- Bad docs → confident wrong answers (and you'll trust them)

> If it's not in the repo, the agent will invent it.

---

## Structure: router + leaves, not one giant file

<div class="columns">

**Anti-pattern**
```
CLAUDE.md  (4,000 lines)
```
- Always loaded
- Burns tokens every turn
- Contradictions pile up
- Nobody updates it

**Pattern**
```
CLAUDE.md (router, ~100 lines)
docs/
  architecture.md
  testing.md
  deploy.md
  domain/
    billing.md
    auth.md
```
The router says: *"for billing questions, read docs/domain/billing.md"*

</div>

---

## What goes in the router

```markdown
# Project router

## Quick facts
- Stack: TypeScript, Postgres, Next.js
- Test command: `npm test`
- Lint: `npm run lint`

## Where to look
- Architecture decisions → `docs/architecture.md`
- Testing conventions → `docs/testing.md`
- Domain: billing → `docs/domain/billing.md`
- Domain: auth → `docs/domain/auth.md`

## House rules
- No `any` in TS
- Prefer composition over inheritance
- Migrations are reviewed by @dba-team
```

Small, stable, and tells the agent **where to read next**.

---

## Why not one big file?

- Every token in the always-loaded context is paid for **every turn**
- Long context degrades reasoning quality (the "lost in the middle" effect)
- Agents skim — they're more likely to actually read a focused 200-line doc
- Humans can review small docs; nobody reviews 4,000-line ones
- Router-style docs survive refactors; monolithic ones rot

---

## Tool tour: 5 to know

| Tool | What it does |
|---|---|
| **Grill-me-with-docs** | Forces the agent to *interview* you before writing code |
| **Get Shit Done (GSD)** | Opinionated workflow for shipping a task end-to-end |
| **OpenSpec** | Spec-first development; the agent works from a spec doc |
| **Superpowers** | A curated bundle of high-quality skills |
| **BTW (`/btw`)** | Side-channel info about the current session, no context poisoning |

We'll demo all five.

---

## Grill-me-with-docs

**Problem:** you give a vague prompt → AI fills the gaps with assumptions → wrong code.

**Fix:** before any code, the skill makes the agent ask you the questions a senior engineer would ask.

- "What's the failure mode you're worried about?"
- "Is this a hot path?"
- "Who else writes to this table?"

You write down what you actually want. Then the code follows.

---

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

## OpenSpec

Spec-first. You write (or generate) a spec markdown, then the agent implements **against the spec, not the chat**.

- Spec is reviewable, diffable, version-controlled
- The agent has a stable target — chat drift doesn't change scope
- When the spec is wrong, you fix the spec, not the code

Great for: anything you'd put in a ticket.

---

## Superpowers

A curated **skill pack**. Think "linter, but for AI workflows."

- Skills for verifying changes
- Skills for security review
- Skills for running the app
- Skills for refactoring chores

You install once, every project benefits.

---

## BTW (`/btw`)

"By the way…" — a way to surface session info *without* polluting the conversation context.

Use cases:
- "What model am I on?"
- "How much context have I used?"
- "What permissions are active?"

The answer comes back as a side panel, not as a message that the next reply has to re-read.

---

## Why too much context is bad

- **Cost** — every token is paid every turn
- **Latency** — bigger prompt = slower response
- **Quality** — models reason worse on long contexts (well-documented effect)
- **Confusion** — old, stale, or contradictory info biases new answers
- **Hidden state** — you lose track of what the model "knows"

> Context is not a junk drawer. It's working memory.

---

## Clear vs compact

<div class="columns">

**Clear the context when**
- Switching tasks
- The agent is stuck in a wrong assumption
- You're about to do something high-stakes
- The conversation is full of dead ends

**Compact the context when**
- You want to keep the *conclusions* but drop the *exploration*
- You're mid-task and approaching limits
- The early turns are no longer relevant but the decisions still are

</div>

> Default: clear more often than you think. Re-establishing context is cheap; cleaning up after a confused agent is not.

---

<!-- _class: lead -->

# Part 2 — Live Demo

I drive. You watch. Questions welcome.

---

## Demo plan

1. `/grill-me-with-docs` on a fake feature request
2. **GSD vs OpenSpec** on the same task — side by side
3. Tour of **Superpowers** skills
4. `/btw` mid-session to check state
5. A real `.claude/CLAUDE.md` router file
6. Doc structure with router + leaves
7. A real subagent markdown file

---

## Demo 1 — Grill me with docs

Prompt I'll use:

> "Add rate limiting to our public API."

Watch what the agent asks back **before** writing a line of code. Notice how the questions surface assumptions I hadn't made.

---

## Demo 2 — GSD vs OpenSpec

Same task: *"Add a `/health` endpoint that checks DB connectivity."*

- **GSD**: chat → implementation → tests → commit
- **OpenSpec**: write spec → review spec → implement spec → tests → commit

Compare:
- Time to first commit
- Reviewability of the artifact
- What happens when I change my mind mid-task

---

## Demo 3 — Superpowers tour

Quick look at what installing Superpowers gives you:

- `verify` — actually run the app to confirm a change works
- `code-review` — review the current diff for bugs
- `security-review` — focused security pass
- `run` — launch the project the right way

We'll trigger `verify` on a real change.

---

## Demo 4 — `/btw`

Mid-demo, I'll run `/btw` to ask:

- What model am I on?
- What permissions are active?
- How much context is left?

Notice how the answer **doesn't** show up as a message the next prompt has to ingest.

---

## Demo 5 — A real CLAUDE.md router

We'll open the project's `CLAUDE.md` and walk through:

- The "quick facts" block
- The routing table to deeper docs
- The "house rules" section
- What is **not** in this file (and why)

---

## Demo 6 — Docs with a router

Repo layout:

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

## Demo 7 — A subagent file

We'll look at `.claude/agents/migration-checker.md`:

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

<!-- _class: lead -->

# Part 3 — Hands-on (do this later)

Reproduce the demos on your machine.

---

## Hands-on setup (5 min)

```bash
# Clone a sandbox project (any small repo of yours works)
git clone <your-repo>
cd <your-repo>

# Install Claude Code (or your tool of choice)
npm install -g @anthropic-ai/claude-code

# Initialize
claude init
```

You should now have a `.claude/` folder and a `CLAUDE.md`.

---

## Exercise 1 — Grill me with docs

1. Install the `grill-me-with-docs` skill
2. Prompt: *"Add a feature flag system to this project."*
3. Let the agent interview you
4. **Save the answers as a spec doc** in `docs/specs/feature-flags.md`
5. Then ask the agent to implement against that doc

> Goal: feel the difference between "vibe coding" and spec-driven prompts.

---

## Exercise 2 — GSD vs OpenSpec

Pick a real small task in your repo.

- Do it once with **GSD**
- Reset, do it again with **OpenSpec**

Compare the diffs and the time. Note which one you'd want for:
- A 30-minute chore
- A 2-day feature
- A risky refactor

---

## Exercise 3 — Install Superpowers

1. Install the Superpowers skill pack
2. Make any small change in your repo
3. Run `/verify` — does it actually launch your app?
4. Run `/code-review` on the diff
5. Run `/security-review`

Notice what each skill is good at — and what it misses.

---

## Exercise 4 — `/btw` discipline

Use `/btw` at least three times during a session:

- Once to check your model
- Once to check context usage
- Once to ask "what files have I touched this session?"

Goal: train the muscle of asking **meta-questions out of band**.

---

## Exercise 5 — Write your CLAUDE.md router

Replace your `CLAUDE.md` with a router-style file:

- ≤100 lines
- Quick facts (stack, test cmd, lint cmd)
- Routing table to `docs/*`
- House rules

Then move detail into `docs/architecture.md`, `docs/testing.md`, etc.

> Bonus: ask the agent to do this *for* you.

---

## Exercise 6 — Router-style docs

Take your biggest existing doc (or your README) and split it:

- One **router** page (titles + one-line summary + link)
- N **leaf** pages, each focused

Re-run a typical prompt and compare:
- Tokens used
- Quality of the answer

---

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

Use it on a real PR. Iterate the description until invocation feels reliable.

---

<!-- _class: lead -->

# Part 4 — Q&A

The questions that actually matter

---

## Do coding standards still matter?

**Short answer:** more than ever.

- The agent will follow whatever pattern dominates the repo
- No standard → it averages across everything it's ever seen
- Standards are how you steer the agent without prompting every time

> Let the AI **execute** the standard. Don't let it **invent** the standard.

---

## Should we change architecture to suit AI?

A bit, yes — but not by inventing new patterns.

**Things that help AI also help humans:**
- Small modules with clear boundaries
- Pure functions where possible
- Explicit dependency injection
- Boring, predictable file layout

**Things that hurt AI:**
- Magic, reflection, dynamic dispatch everywhere
- Implicit conventions ("you just have to know")
- Mega-files of mixed concerns

> If your architecture confuses a new hire, it confuses the agent.

---

## Is testing strategy shifting?

Yes. Two real changes:

1. **More tests, lower cost.** Generating tests is cheap; running them is the new bottleneck.
2. **Tests as specs.** Tests become the contract the agent implements against.

What stays the same:
- You still need to know **what** to test
- Coverage ≠ correctness
- E2E tests still tell you the truth

> The agent is great at writing the tests *you* tell it to write. Mediocre at deciding *which* tests matter.

---

## How to share AI assets across a company

**Commit to the repo:**
- `CLAUDE.md` router
- `docs/*` (the leaf docs)
- `.claude/agents/*` (project-specific subagents)
- `.claude/skills/*` (project-specific skills)
- MCP server *configuration* (not secrets)

**Do NOT commit:**
- API keys, tokens, anything in env vars
- Personal preferences (themes, keybindings)
- Local-only paths
- Anything in `.claude/settings.local.json`

---

## Sharing patterns

<div class="columns">

**Per-project**
- Lives in the repo
- Versioned with the code
- Reviewed in PRs

**Per-person**
- `~/.claude/` for your own skills
- Your preferred subagents
- Keybindings, themes

**Per-organization**
- A "starter pack" repo with house skills
- Internal MCP server for the company API
- Shared `docs/conventions.md` linked from each project

</div>

---

## How I personally share knowledge

- Pair sessions, recorded
- A `docs/learnings/` folder in every project — short notes, dated
- A team channel for "I figured out X today"
- When I do something twice → it becomes a skill, committed
- When I do something thrice → it becomes a subagent

> Tacit knowledge dies. Committed markdown survives team turnover.

---

## How companies usually share (the messy truth)

- Confluence pages nobody reads
- A Slack channel of links nobody bookmarks
- "Ask Bob, he knows"
- Tribal knowledge that walks out when Bob leaves

Agentic workflows make this **worse if you don't fix it**:
- The agent reads the repo, not Confluence
- "Ask Bob" doesn't scale to a parallel fleet of agents

> Repo-resident docs are the only kind that survive.

---

## Risk 1 — Less velocity while feeling more productive

You feel fast. You ship less.

- Time-to-PR is shorter
- Time-to-merged-and-stable is often **longer**
- Rework, debugging, re-prompting eats the gains

**Counter:**
- Measure cycle time, not commits
- Track rework rate
- Treat "looks done" as suspicious until verified

---

## Risk 2 — Knowing architecture, not code

You stop reading the diffs carefully. You drift into being a manager of code.

**This is fine for some tasks. Dangerous for others.**

**Counter:**
- Read every diff line for anything security-, money-, or data-touching
- Periodically write code from scratch to keep the muscle
- Demand the agent explain *why*, not just *what*

---

## Risk 3 — Hallucinations as features

The worst bugs: code that runs, passes tests, and does the wrong thing confidently.

- Made-up API calls that happen to exist
- Plausible-looking math that's subtly off
- "Helpful" extra behavior nobody asked for

**Counter:**
- Spec-first (OpenSpec)
- Property-based tests for risky logic
- Always ask: *"What did you change beyond what I asked?"*

---

## Risk 4 — Security gaps

Agents will happily:
- Disable a CSP header to fix a console error
- `chmod 777` to fix a permission issue
- Skip a hook with `--no-verify` to get a green build
- Hardcode a secret "just for testing"

**Counter:**
- Run `/security-review` on every diff that touches auth, headers, secrets, or infra
- Pre-commit hooks the agent *cannot* bypass
- Code review by a human for security-critical paths

---

## Risk 5 — Large blast radius for small changes

"Refactor this function" → 47 files changed.

**Counter:**
- Constrain scope explicitly in the prompt
- Use `git diff --stat` before accepting
- A skill that rejects diffs touching > N files without confirmation

---

## Risk 6 — Bad code structure costs real money

Every prompt loads context. Bad structure = bigger context = more tokens = more $.

- Monolithic files force the agent to load the whole thing
- Implicit dependencies force exploratory grep
- Inconsistent naming forces more retries

**Counter:**
- Small files
- Explicit imports
- Consistent naming
- Router-style docs

---

## How to protect yourself (summary)

1. **Spec before code** for anything non-trivial
2. **Verify** with the actual app, not just tests
3. **Read diffs** for anything security- or data-critical
4. **Constrain scope** in the prompt
5. **Commit your skills and agents** so the team gets better, not just you
6. **Measure cycle time**, not commits

---

## Debugging while pairing with AI

Three styles, pick by situation:

<div class="columns">

**Prompt-only**
- Fastest for shallow bugs
- Risky: agent guesses
- Good for: "I get error X on line Y"

**Pairing (REPL style)**
- You drive the hypothesis, AI runs the experiments
- Best for: unfamiliar code, unclear failures

</div>

**Test-driven debug**
- Write a failing test that captures the bug first
- Then let the AI fix until green
- Best for: regressions, anything you must not break again

---

## Is your own code easier to debug?

Yes — but the gap is closing.

- **Your code**: you remember the *why*, the intent, the trade-offs
- **AI code**: the agent remembers nothing; you read it cold

Mitigations:
- Have the agent leave **decision notes** in the PR description (not in code comments)
- Force the agent to write the *failing test first*, so intent is captured
- Keep diffs small enough to actually read

> The debug cost is paid where the intent is *unrecorded*. Record intent.

---

<!-- _class: lead -->

# Part 5 — Tips from the people doing this full-time

Links to read after the workshop.

---

## Anthropic — building with Claude

- **Claude Code docs**: https://code.claude.com/docs
- **Engineering blog**: https://www.anthropic.com/engineering
- **Prompt engineering guide**: https://docs.claude.com/en/docs/build-with-claude/prompt-engineering/overview
- **Agent design patterns**: https://www.anthropic.com/engineering/building-effective-agents

> Start here for primary-source guidance.

---

## Simon Willison — the daily field notes

- **Blog**: https://simonwillison.net/
- **"Things I've learned about LLMs"**: https://simonwillison.net/tags/llms/
- **Newsletter** via the blog RSS

Why: he tries everything, writes it down the same day, and is honest about what didn't work.

---

## Andrej Karpathy — the deep intuition

- **YouTube — "Intro to LLMs"**: https://www.youtube.com/watch?v=zjkBMFhNj_g
- **YouTube — "Let's build GPT"**: https://www.youtube.com/watch?v=kCc8FmEb1nY
- **Twitter/X**: @karpathy

Why: you'll understand *why* models behave the way they do, not just how to prompt them.

---

## Latent Space (podcast)

- **Site**: https://www.latent.space/
- Long-form interviews with people building real AI products

Why: hear how teams structure their workflows, what failed, what stuck.

---

## Working in public — devs who post their setups

- **Geoffrey Huntley** — https://ghuntley.com/ (agentic workflows, skills, real cases)
- **Steve Yegge** — long-form essays on AI dev workflows
- **Patrick Collison's reading list** (not AI-only, but tasteful)

Why: watch how senior engineers integrate this into a daily practice, not a demo.

---

## Where to follow news without drowning

- **Hacker News** — the "Show HN" and "Ask HN" threads
- **r/LocalLLaMA** for local/open-weight tooling
- **Anthropic + OpenAI + Google DeepMind** blogs only — skip the rest

> The signal-to-noise ratio in the AI space is brutal. Curate hard.

---

## My one-page distilled advice

1. **Docs are runtime.** Router + leaves. Commit them.
2. **Spec before code** for anything that matters.
3. **Skills compound.** Repeated → skill. Skill → subagent. Subagent → committed.
4. **Read the diff.** Especially for auth, money, data.
5. **Clear context often.** It's cheap to re-establish, expensive to debug.
6. **Measure cycle time, not commits.**
7. **Steal patterns from Anthropic, Simon Willison, Karpathy.** Stop reinventing.

---

<!-- _class: lead -->

# Thank you!

### Questions?

rjp.vroegop@gmail.com

The slides, hands-on, and skill files are in this repo.
