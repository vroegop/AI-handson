---
marp: true
theme: default
paginate: true
size: 16:9
header: 'AI for devs'
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

  /* Terminal mock — fallback for when the live demo would not work */
  .terminal {
    background: #1e1e1e;
    color: #e8e8e8;
    font-family: 'JetBrains Mono', ui-monospace, monospace;
    border-radius: 8px;
    overflow: hidden;
    box-shadow: 0 8px 22px rgba(0,0,0,0.22);
    margin: 0.3em 0 0.2em;
  }
  .terminal-header {
    background: #2d2d2d;
    padding: 8px 14px;
    display: flex;
    align-items: center;
    gap: 7px;
    border-bottom: 1px solid #000;
  }
  .terminal-dot {
    width: 12px; height: 12px; border-radius: 50%; display: inline-block;
  }
  .terminal-dot.r { background: #ff5f57; }
  .terminal-dot.y { background: #febc2e; }
  .terminal-dot.g { background: #28c840; }
  .terminal-title {
    color: #999;
    font-size: 13px;
    margin-left: 10px;
    font-family: 'Inter', sans-serif;
    letter-spacing: 0.02em;
  }
  .terminal-body {
    padding: 16px 22px 20px;
    font-size: 17px;
    line-height: 1.55;
  }
  .terminal-body pre {
    background: transparent;
    border: none;
    padding: 0;
    margin: 0;
    color: inherit;
    font-size: inherit;
    line-height: inherit;
    font-family: 'JetBrains Mono', ui-monospace, monospace;
  }
  .terminal-body pre code { background: transparent; padding: 0; color: inherit; }
  .t-prompt { color: #5fafff; font-weight: 600; }
  .t-user   { color: #f8f8f2; }
  .t-skill  { color: var(--accent); font-weight: 600; }
  .t-out    { color: #cfcfcf; }
  .t-ok     { color: #4ade80; }
  .t-warn   { color: #febc2e; }
  .t-dim    { color: #7a7a7a; font-style: italic; }
  .t-cursor {
    display: inline-block;
    width: 9px; height: 18px;
    background: #e8e8e8;
    vertical-align: -3px;
    animation: t-blink 1s steps(2) infinite;
  }
  @keyframes t-blink { 50% { opacity: 0; } }
  .fallback-kicker {
    font-family: 'Inter', sans-serif;
    font-size: 13px;
    font-weight: 600;
    letter-spacing: 0.18em;
    text-transform: uppercase;
    color: var(--accent);
    margin-bottom: 0.3em;
  }

  /* Interactive terminal — click to reveal next line, scrolls when overflowing */
  .terminal.interactive { position: relative; }
  .t-stream .t-line {
    white-space: pre-wrap;
    margin-top: 0.45em;
  }
  .t-stream .t-line:first-child { margin-top: 0; }
  .t-cursor-line { margin-top: 0.45em; display: block; }

  /* Activated by JS; without JS everything stays visible (PDF stays useful) */
  .terminal.interactive.live .terminal-body {
    height: 360px;
    overflow-y: auto;
    overflow-x: hidden;
    scroll-behavior: smooth;
    cursor: pointer;
    scrollbar-width: none;
  }
  .terminal.interactive.live .terminal-body::-webkit-scrollbar { display: none; }
  .terminal.interactive.live .t-line { display: none; }
  .terminal.interactive.live .t-line.revealed {
    display: block;
    animation: t-fadein 0.18s ease-out;
  }
  .terminal.interactive.live.done .t-cursor-line .t-cursor {
    animation: none;
    opacity: 0.35;
  }

  .t-hint {
    display: none;
    position: absolute;
    bottom: 10px;
    right: 14px;
    color: #d6d6d6;
    font-size: 11px;
    font-family: 'Inter', sans-serif;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    background: rgba(0,0,0,0.55);
    padding: 4px 9px;
    border-radius: 4px;
    pointer-events: none;
    user-select: none;
  }
  .terminal.interactive.live .t-hint { display: inline-block; }
  .terminal.interactive.live.done .t-hint {
    background: rgba(74,222,128,0.16);
    color: #4ade80;
  }
  .t-progress { color: var(--accent); font-weight: 600; }
  @keyframes t-fadein {
    from { opacity: 0; transform: translateY(3px); }
    to   { opacity: 1; transform: translateY(0); }
  }

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

<!-- _class: lead part-concepts -->

<svg class="icon icon-xl" viewBox="0 0 64 64" xmlns="http://www.w3.org/2000/svg">
  <path d="M14 30 L14 50 L50 50 L50 30"/>
  <path d="M8 30 L32 12 L56 30"/>
  <path d="M26 50 L26 38 L38 38 L38 50"/>
</svg>

# AI Hands-on for Developers

### From "AI skeptic" to AI-native engineer

Concepts · Q&A · Tips · Hands-on

---

<!-- _class: bio part-concepts -->

<div class="bio-grid">
<div>

# Randy Vroegop

<div class="role">Developer · AI-native engineering practice</div>

- Lead Dev modernisation @ Konecranes
- 9 years non-AI programming
- 1 year transition to AI driven development
- Java, Web, AWS, Architecture

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

<!-- _class: part-concepts -->

## What you'll leave with

- A mental model for **agents, subagents, MCP, and skills**
- A way to **structure documentation** that agents actually use
- Tools you can use today: **Grill-me-with-docs, GSD, OpenSpec, Superpowers, BTW, Caveman**
- Hands-on exercises you can run on your own laptop
- Honest answers about the **risks** of working this way

---

<!-- _class: part-concepts -->

## Agenda

1. **Concepts** — agents, subagents, MCP, skills, docs
2. **Q&A** — questions that matter, and six honest risks
3. **Tips from the pros** — who to follow, what just shipped
4. **Hands-on** — exercises to run later, on your own laptop

---

<!-- _class: lead part-concepts -->

<div class="kicker">Part 1</div>

# Concepts

<svg width="100%" viewBox="0 0 680 680" role="img" xmlns="http://www.w3.org/2000/svg" style="">
  <title style="fill:rgb(0, 0, 0);stroke:none;color:rgb(255, 255, 255);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto">Concepts icon</title>
  <desc style="fill:rgb(0, 0, 0);stroke:none;color:rgb(255, 255, 255);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto">An outline icon: a central lightbulb connected by short lines to four smaller circles at the corners, representing related concepts.</desc>

  <g fill="none" stroke="currentColor" stroke-width="14" stroke-linecap="round" stroke-linejoin="round" color="var(--color-text-primary)" style="fill:none;stroke:rgb(250, 249, 245);color:rgb(250, 249, 245);stroke-width:14px;stroke-linecap:round;stroke-linejoin:round;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto">

  <line x1="260" y1="260" x2="180" y2="180" style="fill:none;stroke:rgb(250, 249, 245);color:rgb(250, 249, 245);stroke-width:14px;stroke-linecap:round;stroke-linejoin:round;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>
  <line x1="420" y1="260" x2="500" y2="180" style="fill:none;stroke:rgb(250, 249, 245);color:rgb(250, 249, 245);stroke-width:14px;stroke-linecap:round;stroke-linejoin:round;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>
  <line x1="140" y1="540" x2="260" y2="420" style="fill:none;stroke:rgb(250, 249, 245);color:rgb(250, 249, 245);stroke-width:14px;stroke-linecap:round;stroke-linejoin:round;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>
  <line x1="540" y1="540" x2="420" y2="420" style="fill:none;stroke:rgb(250, 249, 245);color:rgb(250, 249, 245);stroke-width:14px;stroke-linecap:round;stroke-linejoin:round;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>

  <circle cx="140" cy="140" r="55" style="fill:none;stroke:rgb(250, 249, 245);color:rgb(250, 249, 245);stroke-width:14px;stroke-linecap:round;stroke-linejoin:round;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>
  <circle cx="540" cy="140" r="55" style="fill:none;stroke:rgb(250, 249, 245);color:rgb(250, 249, 245);stroke-width:14px;stroke-linecap:round;stroke-linejoin:round;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>
  <circle cx="140" cy="540" r="55" style="fill:none;stroke:rgb(250, 249, 245);color:rgb(250, 249, 245);stroke-width:14px;stroke-linecap:round;stroke-linejoin:round;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>
  <circle cx="540" cy="540" r="55" style="fill:none;stroke:rgb(250, 249, 245);color:rgb(250, 249, 245);stroke-width:14px;stroke-linecap:round;stroke-linejoin:round;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>

  <path d="M 245 335&#10;             a 95 95 0 1 1 190 0&#10;             c 0 40 -22 62 -40 82&#10;             c -12 14 -18 26 -18 44&#10;             l 0 18&#10;             l -74 0&#10;             l 0 -18&#10;             c 0 -18 -6 -30 -18 -44&#10;             c -18 -20 -40 -42 -40 -82 z" style="fill:none;stroke:rgb(250, 249, 245);color:rgb(250, 249, 245);stroke-width:14px;stroke-linecap:round;stroke-linejoin:round;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>

  <line x1="305" y1="495" x2="375" y2="495" style="fill:none;stroke:rgb(250, 249, 245);color:rgb(250, 249, 245);stroke-width:14px;stroke-linecap:round;stroke-linejoin:round;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>
  <line x1="312" y1="520" x2="368" y2="520" style="fill:none;stroke:rgb(250, 249, 245);color:rgb(250, 249, 245);stroke-width:14px;stroke-linecap:round;stroke-linejoin:round;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>
  <path d="M 322 540 q 18 18 36 0" style="fill:none;stroke:rgb(250, 249, 245);color:rgb(250, 249, 245);stroke-width:14px;stroke-linecap:round;stroke-linejoin:round;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>
  </g>
</svg>

---

<!-- _class: part-concepts -->

## What is an agent markdown file?

```markdown
---
name: code-reviewer
description: Reviews diffs for correctness bugs.
tools: Read, Grep, Bash
model: sonnet
---

You are a reviewer. Focus on correctness, not style.
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

<br>
<br>
<br>

> `description` isn't human docs — it's how the router decides to delegate.

---

<!-- _class: part-concepts -->

## Setting up subagent documentation

Two failure modes:

1. **Too vague** — "helps with code". Router can't pick it.
2. **Too greedy** — claims everything. Gets called for tasks it can't do.

<br>
<br>
<br>

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

<br>
<br>
<br>

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

<br>
<br>
<br>

> The agent doesn't *know* GitHub — it knows a tool called `create_pull_request`

---

<!-- _class: part-concepts -->

## How agents use skills

A **skill** = a reusable, named playbook the agent loads on demand.

<br>
<br>
<br>

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

> "I just did X three times. Extract it into a skill named `<name>`."

<br>
<br>
<br>

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
- Bad docs → confident wrong answers (and you'll trust them)

<br>
<br>
<br>

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
- Agents skim
- Humans can review small docs; nobody reviews 4,000-line ones

---

<!-- _class: part-concepts -->

## Tool tour: six to know

| Tool | What it does |
|---|---|
| **Grill-me-with-docs** | Forces the agent to *interview* you before writing code |
| **Get Shit Done (GSD)** | Opinionated workflow for shipping a task end-to-end |
| **OpenSpec** | Spec-first development; agent works from a spec doc |
| **Superpowers** | A curated bundle of high-quality skills |
| **BTW (`/btw`)** | Side-channel session info, no context poisoning |
| **Caveman (`/caveman`)** | Ultra-compressed mode — cuts tokens ~75%, accuracy intact |

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

## Grill-me-with-docs — what you'd see

<div class="terminal interactive">
  <div class="terminal-header">
    <span class="terminal-dot r"></span>
    <span class="terminal-dot y"></span>
    <span class="terminal-dot g"></span>
    <span class="terminal-title">~/projects/ikea-manuals — claude</span>
  </div>
  <div class="terminal-body">
    <div class="t-stream">
      <div class="t-line"><span class="t-prompt">$</span> <span class="t-user">claude</span></div>
      <div class="t-line"><span class="t-prompt">&gt;</span> <span class="t-user">/grill-me-with-docs  Build a system so IKEA manuals are easier to use</span></div>
      <div class="t-line"><span class="t-dim">▸ loading skill</span> <span class="t-skill">grill-me-with-docs</span></div>
      <div class="t-line"><span class="t-out">Before I write any code, I need answers:</span></div>
      <div class="t-line">  <span class="t-ok">1.</span> Who's the user — customer at home, or store staff?</div>
      <div class="t-line">  <span class="t-ok">2.</span> What's broken — language, diagrams, ordering?</div>
      <div class="t-line">  <span class="t-ok">3.</span> Source: OCR existing PDFs, or feed from IKEA?</div>
      <div class="t-line">  <span class="t-ok">4.</span> Offline-capable? Multi-language?</div>
      <div class="t-line">  <span class="t-ok">5.</span> What does "done" look like in week 1?</div>
      <div class="t-line"><span class="t-dim">↳ writing answers to</span> <span class="t-user">docs/specs/ikea-manuals.md</span></div>
      <div class="t-line"><span class="t-ok">✓</span> spec ready — run <span class="t-user">/gsd</span> or <span class="t-user">/openspec</span> to implement</div>
      <div class="t-cursor-line"><span class="t-cursor"></span></div>
    </div>
  </div>
  <div class="t-hint"><span class="t-progress">0/0</span></div>
</div>

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

## GSD — no spec? write one first

<div class="terminal interactive">
  <div class="terminal-header">
    <span class="terminal-dot r"></span>
    <span class="terminal-dot y"></span>
    <span class="terminal-dot g"></span>
    <span class="terminal-title">~/projects/ikea-manuals — claude</span>
  </div>
  <div class="terminal-body">
    <div class="t-stream">
      <div class="t-line"><span class="t-prompt">$</span> <span class="t-user">claude</span></div>
      <div class="t-line"><span class="t-prompt">&gt;</span> <span class="t-user">/gsd add OAuth login</span></div>
      <div class="t-line"><span class="t-dim">▸ loading skill</span> <span class="t-skill">gsd</span></div>
      <div class="t-line"><span class="t-warn">⏸</span>  <span class="t-out">Hold up — no spec exists for "OAuth login".</span>
   <span class="t-out">Vague tasks become bad code. Let's write it down first.</span></div>
      <div class="t-line"><span class="t-out">Proposed file:</span> <span class="t-user">docs/specs/oauth-login.md</span></div>
      <div class="t-line">  <span class="t-ok">?</span> provider — google / github / both?
  <span class="t-ok">?</span> session — cookie or JWT?
  <span class="t-ok">?</span> existing users — merge by email or block?
  <span class="t-ok">?</span> scope guard — login only, no signup flow?</div>
      <div class="t-line"><span class="t-dim">↳ writing draft to</span> <span class="t-user">docs/specs/oauth-login.md</span></div>
      <div class="t-line"><span class="t-ok">✓</span> 38-line spec drafted · 4 open questions flagged
<span class="t-dim">↳ review it, then re-run</span> <span class="t-user">/gsd implement docs/specs/oauth-login.md</span></div>
      <div class="t-cursor-line"><span class="t-cursor"></span></div>
    </div>
  </div>
  <div class="t-hint"><span class="t-progress">0/0</span></div>
</div>

> The friction *is* the feature. The spec is reviewable; the chat isn't.

---

<!-- _class: part-concepts -->

## GSD — implementing from a spec

<div class="terminal interactive">
  <div class="terminal-header">
    <span class="terminal-dot r"></span>
    <span class="terminal-dot y"></span>
    <span class="terminal-dot g"></span>
    <span class="terminal-title">~/projects/ikea-manuals — claude</span>
  </div>
  <div class="terminal-body">
    <div class="t-stream">
      <div class="t-line"><span class="t-prompt">$</span> <span class="t-user">claude</span></div>
      <div class="t-line"><span class="t-prompt">&gt;</span> <span class="t-user">/gsd implement docs/specs/ikea-manuals.md</span></div>
      <div class="t-line"><span class="t-dim">▸ loading skill</span> <span class="t-skill">gsd</span></div>
      <div class="t-line"><span class="t-out">Phase 1/4 — restate</span>
   parse PDF → searchable steps → reordered UI</div>
      <div class="t-line"><span class="t-out">Phase 2/4 — files to touch</span>
   <span class="t-ok">+</span> src/parser/pdf.ts
   <span class="t-ok">+</span> src/ui/StepList.tsx
   <span class="t-warn">~</span> src/index.ts</div>
      <div class="t-line"><span class="t-out">Phase 3/4 — execute</span>
   <span class="t-ok">✓</span> parser added       <span class="t-dim">(124 lines)</span>
   <span class="t-ok">✓</span> StepList wired up  <span class="t-dim">(2 files)</span>
   <span class="t-ok">✓</span> tests: 14 passed, 0 failed</div>
      <div class="t-line"><span class="t-out">Phase 4/4 — commit</span>
   <span class="t-skill">chore(ikea):</span> vertical slice for manual reorder</div>
      <div class="t-cursor-line"><span class="t-cursor"></span></div>
    </div>
  </div>
  <div class="t-hint"><span class="t-progress">0/0</span></div>
</div>

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

## OpenSpec — what you'd see

<div class="terminal interactive">
  <div class="terminal-header">
    <span class="terminal-dot r"></span>
    <span class="terminal-dot y"></span>
    <span class="terminal-dot g"></span>
    <span class="terminal-title">~/projects/ikea-manuals — claude</span>
  </div>
  <div class="terminal-body">
    <div class="t-stream">
      <div class="t-line"><span class="t-prompt">$</span> <span class="t-user">claude</span></div>
      <div class="t-line"><span class="t-prompt">&gt;</span> <span class="t-user">/openspec from docs/specs/ikea-manuals.md</span></div>
      <div class="t-line"><span class="t-dim">▸ loading skill</span> <span class="t-skill">openspec</span>
<span class="t-dim">▸ generating</span> <span class="t-user">openspec/ikea-manuals.spec.md</span></div>
      <div class="t-line"><span class="t-out">## Acceptance</span></div>
      <div class="t-line">  <span class="t-ok">·</span> GIVEN a Billy bookcase PDF
    WHEN user opens step 3
    THEN missing screws are listed up-front</div>
      <div class="t-line">  <span class="t-ok">·</span> GIVEN an offline device
    WHEN user requests a language switch
    THEN cached translations render</div>
      <div class="t-line">  <span class="t-ok">·</span> GIVEN a step with multiple parts
    WHEN any part is checked off
    THEN progress persists across reloads</div>
      <div class="t-line"><span class="t-ok">✓</span> spec written — 6 acceptance criteria, 0 ambiguities flagged</div>
      <div class="t-line"><span class="t-dim">↳ review the spec, then run</span> <span class="t-user">/openspec implement</span></div>
      <div class="t-cursor-line"><span class="t-cursor"></span></div>
    </div>
  </div>
  <div class="t-hint"><span class="t-progress">0/0</span></div>
</div>

---

<!-- _class: part-concepts -->

## Superpowers

A curated **skill pack**.

- Skills for planning, exploration, verification
- Skills for security review
- Skills for multi-agent fan out
- Skills for refactoring chores

Install once, every project benefits.

---

<!-- _class: part-concepts -->

## Superpowers — what you'd see

<div class="terminal interactive">
  <div class="terminal-header">
    <span class="terminal-dot r"></span>
    <span class="terminal-dot y"></span>
    <span class="terminal-dot g"></span>
    <span class="terminal-title">~/projects/ikea-manuals — claude</span>
  </div>
  <div class="terminal-body">
    <div class="t-stream">
      <div class="t-line"><span class="t-prompt">$</span> <span class="t-user">claude</span></div>
      <div class="t-line"><span class="t-prompt">&gt;</span> <span class="t-user">/superpowers list</span></div>
      <div class="t-line"><span class="t-dim">▸ loaded skill pack</span> <span class="t-skill">superpowers</span> <span class="t-dim">(12 skills)</span></div>
      <div class="t-line">  <span class="t-ok">verify</span>           run the app, confirm change works
  <span class="t-ok">code-review</span>      review current diff for bugs
  <span class="t-ok">security-review</span>  focused auth / secret / header pass</div>
      <div class="t-line">  <span class="t-ok">run</span>              launch the project the right way
  <span class="t-ok">brainstorm</span>       explore before committing to a design
  <span class="t-ok">tdd</span>              red-green-refactor loop
  <span class="t-dim">…6 more</span></div>
      <div class="t-line"><span class="t-prompt">&gt;</span> <span class="t-user">/verify</span></div>
      <div class="t-line"><span class="t-dim">▸ booting dev server on :5173</span></div>
      <div class="t-line"><span class="t-ok">✓</span> page loads, step reorder works, no console errors
<span class="t-ok">✓</span> screenshot saved → <span class="t-user">.claude/verify/2026-05-26-step-reorder.png</span></div>
      <div class="t-cursor-line"><span class="t-cursor"></span></div>
    </div>
  </div>
  <div class="t-hint"><span class="t-progress">0/0</span></div>
</div>

---

<!-- _class: part-concepts -->

## BTW (`/btw`)

"By the way…"


- "Why did you pick that option"
- "Did you already do X"
- "Did I forget to instruct Y"
- "Should we even continue if I want to achieve Z or should I improve the instructions"

---

<!-- _class: part-concepts -->

## BTW — what you'd see

<div class="terminal interactive">
  <div class="terminal-header">
    <span class="terminal-dot r"></span>
    <span class="terminal-dot y"></span>
    <span class="terminal-dot g"></span>
    <span class="terminal-title">~/projects/ikea-manuals — claude</span>
  </div>
  <div class="terminal-body">
    <div class="t-stream">
      <div class="t-line"><span class="t-prompt">&gt;</span> <span class="t-user">/btw  what model am I on, and how much context is left?</span></div>
      <div class="t-line"><span class="t-dim">▸ side-channel — not added to conversation history</span></div>
      <div class="t-line">  model          <span class="t-ok">claude-opus-4-7</span>  <span class="t-dim">(1M context)</span>
  permissions    Read, Edit, Bash, Grep
  context used   <span class="t-ok">38,420</span> / 1,000,000 tokens  <span class="t-dim">(3.8%)</span></div>
      <div class="t-line">  files touched
    · src/parser/pdf.ts
    · src/ui/StepList.tsx
    · docs/specs/ikea-manuals.md</div>
      <div class="t-line"><span class="t-prompt">&gt;</span> <span class="t-user">/btw  did you skip any tests this session?</span></div>
      <div class="t-line"><span class="t-ok">✓</span> 14 passed · 0 skipped · 0 failed
<span class="t-dim">↳ next prompt won't see this output — your context stays clean</span></div>
      <div class="t-cursor-line"><span class="t-cursor"></span></div>
    </div>
  </div>
  <div class="t-hint"><span class="t-progress">0/0</span></div>
</div>

---

<!-- _class: part-concepts -->

## Caveman (`/caveman`)

Ultra-compressed mode. Same technical accuracy, **~75% fewer tokens**.

- Drops articles, hedging, pleasantries
- Keeps file paths, function names, error messages verbatim
- Best for: long sessions, big refactors, anywhere context is the bottleneck

<div class="columns">
<div>

**Normal**
> "I'll go ahead and update the `parseRow` function in `src/parser.ts` so it handles empty cells correctly."

</div>
<div>

**Caveman**
> "Update parseRow `src/parser.ts` — handle empty cells."

</div>
</div>

---

<!-- _class: part-concepts -->

## Caveman — what you'd see

<div class="terminal interactive">
  <div class="terminal-header">
    <span class="terminal-dot r"></span>
    <span class="terminal-dot y"></span>
    <span class="terminal-dot g"></span>
    <span class="terminal-title">~/projects/ikea-manuals — claude</span>
  </div>
  <div class="terminal-body">
    <div class="t-stream">
      <div class="t-line"><span class="t-prompt">&gt;</span> <span class="t-user">add retry to fetchUser in src/api.ts, 3 attempts, exponential backoff</span></div>
      <div class="t-line"><span class="t-out">I'll go ahead and update the <span class="t-user">fetchUser</span> function in <span class="t-user">src/api.ts</span> so that it retries up to three times with exponential backoff starting at 100ms. I'll also make sure the existing tests still pass and add a new one for the retry path.</span></div>
      <div class="t-line"><span class="t-dim">↳ 84 tokens out</span></div>
      <div class="t-line"><span class="t-prompt">&gt;</span> <span class="t-user">/caveman</span></div>
      <div class="t-line"><span class="t-dim">▸ loading skill</span> <span class="t-skill">caveman</span>
<span class="t-ok">✓</span> mode on. terse. tech accuracy intact.</div>
      <div class="t-line"><span class="t-prompt">&gt;</span> <span class="t-user">add retry to fetchUser in src/api.ts, 3 attempts, exponential backoff</span></div>
      <div class="t-line"><span class="t-out">patched <span class="t-user">src/api.ts</span>. fetchUser: 3 attempts, backoff 100/200/400ms. tests pass (5/5). added retry-path test.</span></div>
      <div class="t-line"><span class="t-dim">↳ 22 tokens out</span> <span class="t-ok">— 74% cut</span></div>
      <div class="t-cursor-line"><span class="t-cursor"></span></div>
    </div>
  </div>
  <div class="t-hint"><span class="t-progress">0/0</span></div>
</div>

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

<!-- _class: lead part-qa -->

<svg class="icon icon-xl" viewBox="0 0 64 64" xmlns="http://www.w3.org/2000/svg">
  <circle cx="32" cy="32" r="24"/>
  <path d="M24 24 C 24 18, 30 16, 32 16 C 36 16, 40 18, 40 24 C 40 30, 32 30, 32 36"/>
  <circle cx="32" cy="44" r="2" fill="currentColor"/>
</svg>

<div class="kicker">Part 2</div>

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

## How I share knowledge

- Sessions like this
- Hands-on workshops
- Hackathons
- Starter pack repo

> Teaching teaches me the most.

---

<!-- _class: part-qa -->

## How companies usually share (the messy truth)

- Confluence pages nobody reads
- A Slack channel of links nobody bookmarks
- "Ask Bob, he knows"
- Tribal knowledge that walks out with Bob

---

<!-- _class: part-qa -->

## How companies should now share

- Set up a confluence MCP
- Generate markdown documentation based on Confluence
- Let agents verify information against the codebase - remove what is stale
- "Ask bob" should become "Grill bob" - the AI can fill the gaps
- Verify and read documentation that is going to assist the AI or it will mess up!

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
- Demand the agent explains *why*, not just *what*

---

<!-- _class: part-qa -->

## Risk 3 — Hallucinations as features

The worst bugs: code that runs, passes tests, and is confidently wrong.

- Made-up API calls that happen to exist
- Plausible-looking math that's subtly off
- "Helpful" extra behavior nobody asked for

**Counter:** spec-first, tests for risky logic, ask *"what did you change beyond what I asked?"*

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
- Work from clean worktrees, read the diff

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

Use `/btw`:

-  to check your model
-  to check context usage
-  to ask "what files have I touched this session?"

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

Use it on a PR. Iterate until invocation feels reliable.

---

<!-- _class: lead part-concepts -->

<svg class="icon icon-xl" viewBox="0 0 64 64" xmlns="http://www.w3.org/2000/svg">
  <path d="M12 20 L 32 36 L 52 20"/>
  <rect x="12" y="14" width="40" height="32" rx="2"/>
</svg>

# Thank you

### Questions?

[randy@vroegop.me](mailto:randy@vroegop.me) · [linkedin/randy-vroegop](https://www.linkedin.com/in/randy-vroegop/) · [github/vroegop](https://github.com/vroegop/AI-handson)

Slides, hands-on exercises and skill files live in this repo.

<script>
(function () {
  // Forward keys clickers and keyboards use to advance — we intercept these
  // only when the active slide has an unfinished terminal.
  var FORWARD_KEYS = { 'PageDown': 1, 'ArrowRight': 1, 'ArrowDown': 1, ' ': 1, 'Spacebar': 1, 'Enter': 1 };

  function advanceTerminal(term) {
    var state = term._tState;
    if (!state || state.step >= state.total) return false;
    state.lines[state.step].classList.add('revealed');
    state.step++;
    var body = state.body;
    requestAnimationFrame(function () { body.scrollTop = body.scrollHeight; });
    if (state.progressEl) state.progressEl.textContent = state.step + '/' + state.total;
    if (state.step >= state.total) term.classList.add('done');
    return true;
  }

  function findActiveSection() {
    // Marp bespoke wraps each <section> in an <svg><foreignObject> and
    // applies .bespoke-marp-active to the SVG wrapper — NOT the <section>.
    // So we match any element with the class, then descend into it.
    var s = document.querySelector('.bespoke-marp-active')
         || document.querySelector('.bespoke-active');
    if (s) return s;
    // Viewport fallback: find the slide wrapper whose center is on screen.
    var wrappers = document.querySelectorAll('.bespoke-marp-slide, .bespoke-slide, [data-marpit-svg]');
    var cx = window.innerWidth / 2, cy = window.innerHeight / 2;
    for (var i = 0; i < wrappers.length; i++) {
      var r = wrappers[i].getBoundingClientRect();
      if (r.width > 0 && r.height > 0 &&
          r.left <= cx && r.right >= cx &&
          r.top  <= cy && r.bottom >= cy) {
        return wrappers[i];
      }
    }
    return null;
  }

  function activeUnfinishedTerminal() {
    var active = findActiveSection();
    // CRITICAL: if no active slide can be identified, return null so forward
    // keys pass through to Marp. Never fall back to document — that would
    // search ALL slides and eat keys globally.
    if (!active) return null;
    var terms = active.querySelectorAll('.terminal.interactive:not(.done)');
    return terms.length ? terms[0] : null;
  }

  function initTerminals() {
    var terms = document.querySelectorAll('.terminal.interactive');
    for (var i = 0; i < terms.length; i++) {
      var term = terms[i];
      if (term.dataset.tInit === '1') continue;
      term.dataset.tInit = '1';
      term.classList.add('live');

      var lines = term.querySelectorAll('.t-line');
      term._tState = {
        step: 0,
        total: lines.length,
        lines: lines,
        body: term.querySelector('.terminal-body'),
        progressEl: term.querySelector('.t-progress')
      };

      // Pre-reveal the first line so the terminal isn't blank on load.
      advanceTerminal(term);

      term.addEventListener('click', function (e) {
        e.stopPropagation();
        e.preventDefault();
        advanceTerminal(this);
      });
    }
  }

  // Capture-phase keydown so we run BEFORE bespoke's slide-advance handler.
  document.addEventListener('keydown', function (e) {
    if (!FORWARD_KEYS[e.key]) return;
    var term = activeUnfinishedTerminal();
    if (!term) return;
    if (advanceTerminal(term)) {
      e.preventDefault();
      e.stopPropagation();
      if (typeof e.stopImmediatePropagation === 'function') e.stopImmediatePropagation();
    }
  }, true);

  if (document.readyState === 'loading') {
    document.addEventListener('DOMContentLoaded', initTerminals);
  } else {
    initTerminals();
  }
  // Marp's bespoke renderer may inject slides after load — re-scan a couple of times.
  setTimeout(initTerminals, 200);
  setTimeout(initTerminals, 1000);
})();
</script>
