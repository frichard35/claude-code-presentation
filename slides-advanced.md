---
theme: seriph
title: "Claude Code: Under the Hood"
info: |
  ## Claude Code: Under the Hood
  LLM interactions, tooling innovations, and ecosystem terminology
class: text-center hero-slide
drawings:
  persist: false
transition: slide-left
mdc: true
duration: 25min
fonts:
  sans: 'Inter'
  serif: 'Inter'
  mono: 'Fira Code'
css: unocss
---

<div class="hero-background"></div>

<div class="hero-content">
  <h1 class="hero-title">Claude Code</h1>
  <h2 class="hero-subtitle">Under the Hood</h2>
  <p class="hero-description">LLM Internals · Innovations · Ecosystem</p>
</div>

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-4 py-2 rounded-lg cursor-pointer hero-button">
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div>

<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700;800&family=Fira+Code:wght@400;500&display=swap');

html {
  background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%) !important;
}

html::after {
  content: '';
  position: fixed;
  top: 0; left: 0; right: 0; bottom: 0;
  background-image:
    radial-gradient(circle at 20% 30%, rgba(0, 156, 109, 0.04) 0%, transparent 50%),
    radial-gradient(circle at 80% 70%, rgba(0, 156, 109, 0.06) 0%, transparent 50%),
    linear-gradient(90deg, rgba(0, 156, 109, 0.015) 1px, transparent 1px),
    linear-gradient(rgba(0, 156, 109, 0.015) 1px, transparent 1px);
  background-size: 100% 100%, 100% 100%, 60px 60px, 60px 60px;
  pointer-events: none;
  z-index: 0;
}

body, #slideshow, .slidev-page, .slidev-layout {
  background: transparent !important;
}

.hero-slide { position: relative; }

.hero-background {
  position: absolute; top: 0; left: 0; right: 0; bottom: 0;
  background: linear-gradient(135deg, #009c6d 0%, #006b4d 100%);
  z-index: -1;
}

.hero-content { margin-top: 8rem; position: relative; z-index: 1; }

.hero-title {
  font-family: 'Inter', sans-serif; font-size: 5rem; font-weight: 800;
  background: linear-gradient(135deg, #ffffff 0%, #f0f0f0 100%);
  -webkit-background-clip: text; -webkit-text-fill-color: transparent;
  background-clip: text; margin-bottom: 0.5rem; letter-spacing: -0.02em;
  filter: drop-shadow(0 2px 40px rgba(255, 255, 255, 0.3));
}

.hero-subtitle {
  font-family: 'Inter', sans-serif; font-size: 2rem; font-weight: 600;
  color: rgba(255, 255, 255, 0.9); margin-bottom: 1rem; letter-spacing: 0.02em;
}

.hero-description {
  font-family: 'Inter', sans-serif; font-size: 1.25rem; font-weight: 300;
  color: rgba(255, 255, 255, 0.7); letter-spacing: 0.03em;
}

.hero-button {
  background: rgba(255, 255, 255, 0.1); backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.2); color: white;
  font-family: 'Inter', sans-serif; font-weight: 500;
  transition: all 0.3s ease; position: relative; z-index: 1;
}

.hero-button:hover {
  background: rgba(255, 255, 255, 0.2); transform: translateY(-2px);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.2);
}
</style>

---
layout: center
class: text-center
---

# Agenda

<div class="grid grid-cols-3 gap-8 pt-8">

<div v-click>
  <div class="text-4xl mb-2">🔄</div>
  <div class="text-xl font-bold mb-2">LLM Communication</div>
  <div class="text-sm opacity-75">Stateless requests, tool use & token growth</div>
  <div class="text-xs opacity-50 mt-1">8 minutes</div>
</div>

<div v-click>
  <div class="text-4xl mb-2">🚀</div>
  <div class="text-xl font-bold mb-2">Innovations</div>
  <div class="text-sm opacity-75">Anthropic's tooling & token optimizations</div>
  <div class="text-xs opacity-50 mt-1">6 minutes</div>
</div>

<div v-click>
  <div class="text-4xl mb-2">🧩</div>
  <div class="text-xl font-bold mb-2">Ecosystem</div>
  <div class="text-sm opacity-75">Tools, hooks, MCP, skills, agents, plugins</div>
  <div class="text-xs opacity-50 mt-1">12 minutes</div>
</div>

</div>

---
layout: section
---

# Part 1: How LLMs Communicate

Stateless Requests · Tool Use · Token Consumption

---

# Turn 1 — "hello"

<div class="token-badge">~200 tokens</div>

<div class="grid grid-cols-2 gap-6 mt-2">

<div>

**→ Request**

```json
{
  "messages": [
    {
      "role": "system",
      "content": "You are Claude Code, an AI
        assistant for software development..."
    },
    {
      "role": "user",
      "content": "hello"
    }
  ],
  "tools": [
    {
      "name": "read_file",
      "description": "Read the content of a file",
      "parameters": {
        "filepath": "string (required)"
      }
    }
  ]
}
```

</div>

<div v-click>

**← Response**

```json
{
  "message": "Hi, how are you?"
}
```

<div class="teaching-point mt-4">
  💡 Tools are always sent with the request,<br/>even when not needed
</div>

</div>

</div>

<style>
.token-badge {
  position: absolute; top: 1.2rem; right: 1.5rem;
  background: #009c6d; color: white;
  padding: 0.2rem 0.8rem; border-radius: 9999px;
  font-size: 0.75rem; font-weight: 600; font-family: 'Fira Code', monospace;
}
.teaching-point {
  background: rgba(0, 156, 109, 0.1);
  border-left: 3px solid #009c6d;
  padding: 0.6rem 0.8rem;
  border-radius: 4px;
  font-size: 0.78rem;
  line-height: 1.5;
}
</style>

---

# Turn 2 — Translate the file

<div class="token-badge token-badge-warning">~400 tokens ↑</div>

<div class="grid grid-cols-2 gap-6 mt-2">

<div>

**→ Request** <span class="stateless-label">Full history resent!</span>

```json {1-12|13-16}
{
  "messages": [
    { "role": "system", "content": "You are Claude Code..." },
    { "role": "user", "content": "hello" },
    {
      "role": "assistant",
      "content": "Hi, how are you?"
    },
    {
      "role": "user",
      "content": "Can you translate in French
        the text inside enUS.txt?"
    }
  ],
  "tools": [{ "name": "read_file", ... }]
}
```

</div>

<div v-click>

**← Response** — Tool call

```json
{
  "tool_use": {
    "name": "read_file",
    "input": {
      "filepath": "enUS.txt"
    }
  }
}
```

<div class="teaching-point mt-4">
  💡 The LLM <strong>doesn't execute tools itself</strong><br/>
  — it asks the harness to do it
</div>

</div>

</div>

<style>
.token-badge {
  position: absolute; top: 1.2rem; right: 1.5rem;
  background: #009c6d; color: white;
  padding: 0.2rem 0.8rem; border-radius: 9999px;
  font-size: 0.75rem; font-weight: 600; font-family: 'Fira Code', monospace;
}
.token-badge-warning { background: #d97706; }
.stateless-label {
  display: inline-block;
  background: rgba(217, 119, 6, 0.15);
  color: #d97706;
  border: 1px solid #d97706;
  padding: 0.1rem 0.5rem;
  border-radius: 4px;
  font-size: 0.65rem;
  font-weight: 600;
  vertical-align: middle;
  margin-left: 0.5rem;
}
.teaching-point {
  background: rgba(0, 156, 109, 0.1);
  border-left: 3px solid #009c6d;
  padding: 0.6rem 0.8rem;
  border-radius: 4px;
  font-size: 0.78rem;
  line-height: 1.5;
}
</style>

---

# Turn 3 — Tool result & final answer

<div class="token-badge token-badge-danger">~600 tokens ↑↑</div>

<div class="grid grid-cols-2 gap-6 mt-2">

<div>

**→ Request** <span class="stateless-label">Full history resent again!</span>

```json {1-16|17-20}
{
  "messages": [
    { "role": "system", "content": "You are Claude Code..." },
    { "role": "user", "content": "hello" },
    { "role": "assistant", "content": "Hi, how are you?" },
    { "role": "user", "content": "Can you translate...enUS.txt?" },
    {
      "role": "assistant",
      "tool_use": { "name": "read_file",
                    "input": { "filepath": "enUS.txt" } }
    },
    {
      "role": "tool",
      "content": "Welcome to Cardif"
    }
  ],
  "tools": [{ "name": "read_file", ... }]
}
```

</div>

<div v-click>

**← Response** — Final answer

```json
{
  "message": "Here is the translation:
    \"Bienvenue à Cardif\""
}
```

<div class="teaching-point mt-4">
  💡 Token count grows at every round-trip.<br/>
  Context = money + latency + limits.
</div>

</div>

</div>

<style>
.token-badge {
  position: absolute; top: 1.2rem; right: 1.5rem;
  background: #009c6d; color: white;
  padding: 0.2rem 0.8rem; border-radius: 9999px;
  font-size: 0.75rem; font-weight: 600; font-family: 'Fira Code', monospace;
}
.token-badge-danger { background: #dc2626; }
.stateless-label {
  display: inline-block;
  background: rgba(220, 38, 38, 0.12);
  color: #dc2626;
  border: 1px solid #dc2626;
  padding: 0.1rem 0.5rem;
  border-radius: 4px;
  font-size: 0.65rem;
  font-weight: 600;
  vertical-align: middle;
  margin-left: 0.5rem;
}
.teaching-point {
  background: rgba(0, 156, 109, 0.1);
  border-left: 3px solid #009c6d;
  padding: 0.6rem 0.8rem;
  border-radius: 4px;
  font-size: 0.78rem;
  line-height: 1.5;
}
</style>

---
layout: section
---

# Part 2: Anthropic Innovations

Solving the Token & Tooling Challenge

---

# 5 Optimizations

<div class="grid grid-cols-5 gap-3 mt-6">

<div v-click class="innov-card">
  <div class="innov-num">1</div>
  <div class="innov-title">Programmatic<br/>Tool Calling</div>
  <div class="innov-badge innov-badge-token">-37% tokens</div>
  <div class="innov-desc">Code instead of JSON to orchestrate tools</div>
</div>

<div v-click class="innov-card">
  <div class="innov-num">2</div>
  <div class="innov-title">Dynamic<br/>Filtering</div>
  <div class="innov-badge innov-badge-token">-24% tokens</div>
  <div class="innov-desc">Filter HTML before sending to model</div>
</div>

<div v-click class="innov-card">
  <div class="innov-num">3</div>
  <div class="innov-title">Tool<br/>Search</div>
  <div class="innov-badge innov-badge-token">-85% context</div>
  <div class="innov-desc">Load tool schemas on demand</div>
</div>

<div v-click class="innov-card">
  <div class="innov-num">4</div>
  <div class="innov-title">Input<br/>Examples</div>
  <div class="innov-badge innov-badge-acc">72% → 90%</div>
  <div class="innov-desc">Examples for complex tool parameters</div>
</div>

<div v-click class="innov-card innov-card-ext">
  <div class="innov-num">5</div>
  <div class="innov-title">LSP<br/>Plugin</div>
  <div class="innov-badge innov-badge-ext">Not Anthropic</div>
  <div class="innov-desc">IDE-like code navigation for LLMs</div>
</div>

</div>

<style>
.innov-card {
  border: 2px solid #8dc9ab; border-radius: 8px;
  padding: 0.8rem 0.6rem; text-align: center;
  display: flex; flex-direction: column; align-items: center; gap: 0.4rem;
}
.innov-card-ext { border-color: #a78bfa; }
.innov-num {
  font-size: 1.5rem; font-weight: 800; color: #8dc9ab; line-height: 1;
}
.innov-card-ext .innov-num { color: #a78bfa; }
.innov-title { font-size: 0.78rem; font-weight: 700; line-height: 1.3; }
.innov-badge {
  font-size: 0.65rem; font-weight: 700; padding: 0.15rem 0.5rem;
  border-radius: 9999px; white-space: nowrap;
}
.innov-badge-token { background: rgba(0, 156, 109, 0.15); color: #009c6d; }
.innov-badge-acc { background: rgba(37, 99, 235, 0.15); color: #2563eb; }
.innov-badge-ext { background: rgba(167, 139, 250, 0.15); color: #7c3aed; }
.innov-desc { font-size: 0.68rem; opacity: 0.75; line-height: 1.3; }
</style>

---

# Token Savings — How it works

<div class="grid grid-cols-3 gap-5 mt-4">

<div v-click class="detail-card">
  <div class="detail-header">
    <span class="detail-num">1</span>
    <span class="detail-name">Programmatic Tool Calling</span>
  </div>
  <div class="detail-body">
    Instead of calling tools one by one through JSON, Claude writes <strong>code</strong> that orchestrates multiple tools. Only the final result enters the context.
  </div>
  <div class="detail-stat">
    43,588 → 27,297 tokens<br/>
    <span class="detail-highlight">-37% on complex tasks</span>
  </div>
</div>

<div v-click class="detail-card">
  <div class="detail-header">
    <span class="detail-num">2</span>
    <span class="detail-name">Dynamic Filtering</span>
  </div>
  <div class="detail-body">
    Automatically filters irrelevant HTML content <strong>before</strong> sending to the model. Only meaningful text reaches the context window.
  </div>
  <div class="detail-stat">
    <span class="detail-highlight">-24% tokens</span><br/>
    on web content tasks
  </div>
</div>

<div v-click class="detail-card">
  <div class="detail-header">
    <span class="detail-num">3</span>
    <span class="detail-name">Tool Search</span>
  </div>
  <div class="detail-body">
    Tools are marked <code>defer_loading: true</code>. Only tool <em>names</em> are loaded initially. Full schemas are fetched on demand via a search tool.
  </div>
  <div class="detail-stat">
    72K → 3.5K tokens for 50+ tools<br/>
    <span class="detail-highlight">-85% context usage</span>
  </div>
</div>

</div>

<style>
.detail-card {
  border: 1px solid rgba(141, 201, 171, 0.4);
  border-radius: 8px; padding: 1rem;
  background: rgba(141, 201, 171, 0.05);
  display: flex; flex-direction: column; gap: 0.6rem;
}
.detail-header {
  display: flex; align-items: center; gap: 0.5rem;
}
.detail-num {
  background: #009c6d; color: white;
  width: 1.4rem; height: 1.4rem; border-radius: 50%;
  display: flex; align-items: center; justify-content: center;
  font-size: 0.75rem; font-weight: 700; flex-shrink: 0;
}
.detail-name { font-size: 0.85rem; font-weight: 700; }
.detail-body { font-size: 0.75rem; opacity: 0.85; line-height: 1.45; }
.detail-body code {
  background: rgba(0,0,0,0.08); padding: 0 0.3rem;
  border-radius: 3px; font-family: 'Fira Code', monospace; font-size: 0.7rem;
}
.detail-stat {
  font-size: 0.72rem; font-family: 'Fira Code', monospace;
  border-top: 1px solid rgba(141, 201, 171, 0.3);
  padding-top: 0.5rem; line-height: 1.5;
}
.detail-highlight { color: #009c6d; font-weight: 700; }
</style>

---

# Accuracy & Navigation

<div class="grid grid-cols-2 gap-8 mt-6">

<div v-click class="detail-card">
  <div class="detail-header">
    <span class="detail-num">4</span>
    <span class="detail-name">Input Examples</span>
  </div>
  <div class="detail-body">
    <p>JSON schemas define structure, but can't convey <strong>usage patterns</strong>. The new <code>input_examples</code> field shows the model how to use complex tools correctly.</p>

```json
{
  "name": "query_db",
  "input_examples": [
    { "table": "users", "filter": "active=true",
      "limit": 10 }
  ]
}
```

  </div>
  <div class="detail-stat">
    Accuracy: <span class="detail-highlight">72% → 90%</span> on complex parameters
  </div>
</div>

<div v-click class="detail-card detail-card-ext">
  <div class="detail-header">
    <span class="detail-num detail-num-ext">5</span>
    <span class="detail-name">LSP Plugin</span>
    <span class="ext-badge">Not Anthropic</span>
  </div>
  <div class="detail-body">
    <p>Language Server Protocol integration gives Claude IDE-like code intelligence:</p>
    <ul>
      <li>Go-to-definition</li>
      <li>Find all references</li>
      <li>Symbol search across codebase</li>
      <li>Type information</li>
    </ul>
    <p class="mt-2">Lets the LLM navigate large codebases efficiently without reading every file.</p>
  </div>
</div>

</div>

<style>
.detail-card {
  border: 1px solid rgba(141, 201, 171, 0.4);
  border-radius: 8px; padding: 1rem;
  background: rgba(141, 201, 171, 0.05);
  display: flex; flex-direction: column; gap: 0.6rem;
}
.detail-card-ext {
  border-color: rgba(167, 139, 250, 0.4);
  background: rgba(167, 139, 250, 0.05);
}
.detail-header {
  display: flex; align-items: center; gap: 0.5rem;
}
.detail-num {
  background: #009c6d; color: white;
  width: 1.4rem; height: 1.4rem; border-radius: 50%;
  display: flex; align-items: center; justify-content: center;
  font-size: 0.75rem; font-weight: 700; flex-shrink: 0;
}
.detail-num-ext { background: #7c3aed; }
.detail-name { font-size: 0.85rem; font-weight: 700; }
.ext-badge {
  background: rgba(167, 139, 250, 0.15); color: #7c3aed;
  font-size: 0.6rem; font-weight: 700; padding: 0.1rem 0.4rem;
  border-radius: 9999px; margin-left: auto;
}
.detail-body { font-size: 0.75rem; opacity: 0.85; line-height: 1.45; }
.detail-body ul { padding-left: 1.2rem; margin: 0.3rem 0; }
.detail-body li { margin-bottom: 0.2rem; }
.detail-body code {
  background: rgba(0,0,0,0.08); padding: 0 0.3rem;
  border-radius: 3px; font-family: 'Fira Code', monospace; font-size: 0.7rem;
}
.detail-stat {
  font-size: 0.72rem; font-family: 'Fira Code', monospace;
  border-top: 1px solid rgba(141, 201, 171, 0.3);
  padding-top: 0.5rem;
}
.detail-highlight { color: #009c6d; font-weight: 700; }
</style>

---
layout: section
---

# Part 3: Claude Code Ecosystem

Understanding the Terminology

---

# Tool · Command · Hook

<div class="grid grid-cols-3 gap-5 mt-4">

<div v-click class="term-card term-card-green">
  <div class="term-icon">🔧</div>
  <h3 class="term-title">Tool</h3>
  <p class="term-desc">Functions exposed to the LLM. The model calls them via structured JSON. The <strong>harness executes</strong> and returns results.</p>
  <div class="term-examples">
    <code>Read</code> <code>Edit</code> <code>Bash</code><br/>
    <code>Grep</code> <code>Glob</code> <code>Write</code>
  </div>
</div>

<div v-click class="term-card term-card-blue">
  <div class="term-icon">⌨️</div>
  <h3 class="term-title">Command</h3>
  <p class="term-desc">User-facing <code>/slash</code> shortcuts. Handled by the harness <strong>before</strong> the LLM. Some map to Skills.</p>
  <div class="term-examples">
    <code>/help</code> <code>/clear</code> <code>/compact</code><br/>
    <code>/agents</code> <code>/mcp</code> <code>/hooks</code>
  </div>
</div>

<div v-click class="term-card term-card-orange">
  <div class="term-icon">⚡</div>
  <h3 class="term-title">Hook</h3>
  <p class="term-desc">Deterministic scripts triggered at lifecycle events. Configured in <code>settings.json</code>. Runs <strong>outside the agentic loop</strong>.</p>
  <div class="term-events">
    PreToolUse · PostToolUse<br/>
    SessionStart · Stop · UserPromptSubmit
  </div>
  <div class="isolated-badge">ISOLATED — no shared context</div>
</div>

</div>

<style>
.term-card {
  border-radius: 8px; padding: 1rem;
  display: flex; flex-direction: column; gap: 0.5rem;
  border-left: 4px solid;
}
.term-card-green { border-color: #009c6d; background: rgba(0, 156, 109, 0.06); }
.term-card-blue { border-color: #2563eb; background: rgba(37, 99, 235, 0.06); }
.term-card-orange { border-color: #d97706; background: rgba(217, 119, 6, 0.06); }
.term-icon { font-size: 1.8rem; }
.term-title { font-size: 1rem; font-weight: 700; margin: 0; }
.term-desc { font-size: 0.75rem; line-height: 1.45; opacity: 0.9; }
.term-desc code, .term-examples code {
  background: rgba(0,0,0,0.08); padding: 0 0.3rem;
  border-radius: 3px; font-family: 'Fira Code', monospace; font-size: 0.68rem;
}
.term-examples {
  font-size: 0.72rem; line-height: 1.8;
}
.term-events {
  font-size: 0.68rem; font-family: 'Fira Code', monospace;
  opacity: 0.75; line-height: 1.6;
}
.isolated-badge {
  background: rgba(220, 38, 38, 0.12); color: #dc2626;
  border: 1px solid rgba(220, 38, 38, 0.3);
  padding: 0.2rem 0.5rem; border-radius: 4px;
  font-size: 0.65rem; font-weight: 700; text-align: center;
}
</style>

---

# MCP Servers

<div class="not-only-badge">not only in Claude Code</div>

<div class="grid grid-cols-2 gap-8 mt-4">

<div v-click>

**Model Context Protocol** — open standard for AI-tool integrations.

Called **connectors** or **extensions** depending on context.

Connects Claude to external systems:
databases, APIs, SaaS tools, browsers...

```
MCP Host (Claude Code)
    └─ MCP Client ──── MCP Server (e.g. Postgres)
    └─ MCP Client ──── MCP Server (e.g. GitHub)
    └─ MCP Client ──── MCP Server (e.g. Slack)
```

</div>

<div v-click>

**6 primitives**

<div class="prim-group">
  <div class="prim-label">Server → Client</div>
  <div class="prim-items">
    <span class="prim prim-green">Tools</span>
    <span class="prim prim-green">Resources</span>
    <span class="prim prim-green">Prompts</span>
  </div>
</div>

<div class="prim-group mt-3">
  <div class="prim-label">Client → Server</div>
  <div class="prim-items">
    <span class="prim prim-blue">Sampling</span>
    <span class="prim prim-blue">Elicitation</span>
    <span class="prim prim-blue">Logging</span>
  </div>
</div>

<div class="prim-group mt-3">
  <div class="prim-label">Utility</div>
  <div class="prim-items">
    <span class="prim prim-gray">Tasks <em style="font-size:0.6rem">(experimental)</em></span>
  </div>
</div>

</div>

</div>

<style>
.not-only-badge {
  position: absolute; top: 1.2rem; right: 1.5rem;
  background: rgba(167, 139, 250, 0.15); color: #7c3aed;
  border: 1px solid rgba(167, 139, 250, 0.4);
  padding: 0.2rem 0.7rem; border-radius: 9999px;
  font-size: 0.65rem; font-weight: 600;
}
.prim-group { display: flex; flex-direction: column; gap: 0.3rem; }
.prim-label { font-size: 0.68rem; opacity: 0.6; font-weight: 600; text-transform: uppercase; letter-spacing: 0.05em; }
.prim-items { display: flex; gap: 0.4rem; flex-wrap: wrap; }
.prim {
  padding: 0.2rem 0.6rem; border-radius: 9999px;
  font-size: 0.75rem; font-weight: 600;
}
.prim-green { background: rgba(0, 156, 109, 0.15); color: #009c6d; }
.prim-blue { background: rgba(37, 99, 235, 0.15); color: #2563eb; }
.prim-gray { background: rgba(100, 116, 139, 0.15); color: #475569; }
</style>

---

# Skills

<div class="not-only-badge">not only in Claude Code</div>

<div class="grid grid-cols-2 gap-8 mt-4">

<div v-click>

A **SKILL.md** file with YAML frontmatter + markdown instructions.

```yaml
---
name: deploy
description: Deploy the application to production
disable-model-invocation: true
allowed-tools: Bash
---

Deploy to production:
1. Run tests
2. Build the application
3. Push to deployment target
```

Two invocation modes:
- **User-invocable**: `/deploy` (you trigger it)
- **Model-invocable**: Claude loads it automatically

Follows the **Agent Skills** open standard (`agentskills.io`)

</div>

<div v-click>

**Skills can contain multiple files:**

```
my-skill/
├── SKILL.md         ← main instructions (required)
├── templates/
│   └── config.yaml  ← templates for Claude
├── scripts/
│   └── validate.sh  ← scripts Claude can run
└── examples/
    └── sample.md    ← few-shot examples
```

<div class="skills-community mt-4">
  🌐 Community skills available at <strong>skills.sh</strong>
</div>

</div>

</div>

<style>
.not-only-badge {
  position: absolute; top: 1.2rem; right: 1.5rem;
  background: rgba(167, 139, 250, 0.15); color: #7c3aed;
  border: 1px solid rgba(167, 139, 250, 0.4);
  padding: 0.2rem 0.7rem; border-radius: 9999px;
  font-size: 0.65rem; font-weight: 600;
}
.skills-community {
  background: rgba(0, 156, 109, 0.1);
  border: 1px solid rgba(0, 156, 109, 0.3);
  padding: 0.6rem 0.8rem; border-radius: 6px;
  font-size: 0.8rem;
}
</style>

---

# Agents & Sub-agents

<div class="grid grid-cols-2 gap-6 mt-4">

<div v-click>

**Built-in agents**

<div class="agent-card">
  <span class="agent-name">Explore</span>
  <span class="agent-model">Haiku</span>
  <span class="agent-tools">read-only tools</span>
  <span class="agent-desc">Fast codebase search & analysis</span>
</div>

<div class="agent-card">
  <span class="agent-name">Plan</span>
  <span class="agent-model">inherits</span>
  <span class="agent-tools">read-only tools</span>
  <span class="agent-desc">Research for plan mode</span>
</div>

<div class="agent-card">
  <span class="agent-name">General-purpose</span>
  <span class="agent-model">inherits</span>
  <span class="agent-tools">all tools</span>
  <span class="agent-desc">Complex multi-step tasks</span>
</div>

<div class="mt-3 text-xs opacity-60">
  + Custom agents: own system prompt, tool restrictions, model choice
</div>

</div>

<div v-click>

**Isolation model**

<div class="isolated-big-badge">ISOLATED</div>

Each sub-agent runs in its **own context window**:
- Does not inherit conversation history
- Results are **summarized** back to the parent
- Cannot spawn other sub-agents (no nesting)

**Agent Teams** *(experimental)*: independent sessions that communicate with each other directly — peer-to-peer, not parent-child.

</div>

</div>

<style>
.agent-card {
  display: grid; grid-template-columns: auto auto auto 1fr;
  align-items: center; gap: 0.4rem;
  padding: 0.5rem 0.7rem; margin-bottom: 0.4rem;
  background: rgba(0, 156, 109, 0.07);
  border: 1px solid rgba(141, 201, 171, 0.3);
  border-radius: 6px;
}
.agent-name { font-weight: 700; font-size: 0.8rem; }
.agent-model {
  background: rgba(37, 99, 235, 0.12); color: #2563eb;
  font-size: 0.6rem; font-weight: 600; padding: 0.1rem 0.4rem;
  border-radius: 9999px; white-space: nowrap;
}
.agent-tools {
  background: rgba(100, 116, 139, 0.12); color: #475569;
  font-size: 0.6rem; font-weight: 600; padding: 0.1rem 0.4rem;
  border-radius: 9999px; white-space: nowrap;
}
.agent-desc { font-size: 0.7rem; opacity: 0.7; text-align: right; }
.isolated-big-badge {
  background: rgba(220, 38, 38, 0.1); color: #dc2626;
  border: 2px solid rgba(220, 38, 38, 0.3);
  padding: 0.4rem 1rem; border-radius: 6px;
  font-size: 0.9rem; font-weight: 800; text-align: center;
  margin-bottom: 1rem; letter-spacing: 0.05em;
}
</style>

---

# Marketplace & Plugins

<div class="grid grid-cols-2 gap-8 mt-4">

<div v-click>

A **Plugin** is the packaging layer that bundles:

<div class="plugin-items">
  <div class="plugin-item">🧠 Skills</div>
  <div class="plugin-item">⚡ Hooks</div>
  <div class="plugin-item">🤖 Agents</div>
  <div class="plugin-item">🔌 MCP Servers</div>
  <div class="plugin-item">📝 LSP Servers</div>
  <div class="plugin-item">⚙️ Settings</div>
</div>

Skills are **namespaced** to avoid conflicts:

```
/my-plugin:deploy
/my-plugin:review
```

</div>

<div v-click>

**Plugin structure:**

```
my-plugin/
├── .claude-plugin/
│   └── plugin.json    ← manifest (name, version...)
├── skills/
├── agents/
├── commands/
├── hooks/
├── .mcp.json
├── .lsp.json
├── bin/               ← added to PATH
└── settings.json
```

**Marketplace** = catalog distributing plugins

Sources: GitHub · npm · git URL · local path

Submit to the official Anthropic marketplace at<br/>
`claude.ai/settings/plugins/submit`

</div>

</div>

<style>
.plugin-items {
  display: grid; grid-template-columns: 1fr 1fr;
  gap: 0.4rem; margin: 0.8rem 0;
}
.plugin-item {
  background: rgba(0, 156, 109, 0.08);
  border: 1px solid rgba(141, 201, 171, 0.3);
  border-radius: 6px; padding: 0.4rem 0.7rem;
  font-size: 0.8rem; font-weight: 500;
}
</style>

---
layout: center
class: text-center
---

# Questions?

<div class="mt-8 text-lg opacity-75">
  This presentation was built WITH Claude Code
</div>

<PoweredBySlidev mt-10 />

<!-- Global styles -->
<style global>
html, body, #app, #page-root {
  background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%) !important;
}

body::after {
  content: '';
  position: fixed; top: 0; left: 0; right: 0; bottom: 0;
  background-image:
    radial-gradient(circle at 20% 30%, rgba(0, 156, 109, 0.04) 0%, transparent 50%),
    radial-gradient(circle at 80% 70%, rgba(0, 156, 109, 0.06) 0%, transparent 50%),
    linear-gradient(90deg, rgba(0, 156, 109, 0.015) 1px, transparent 1px),
    linear-gradient(rgba(0, 156, 109, 0.015) 1px, transparent 1px);
  background-size: 100% 100%, 100% 100%, 60px 60px, 60px 60px;
  pointer-events: none; z-index: 0;
}

#slideshow { position: relative; z-index: 1; }

.slidev-page:not(.slidev-page-1),
.slidev-page:not(.slidev-page-1) .slidev-layout {
  background: transparent !important;
}
</style>
