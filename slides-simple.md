---
theme: seriph
title: "The Engine & the Chassis"
info: |
  ## The Engine & the Chassis
  How We Talk to AI Today — Agentic tools, MCP servers & Agent Skills
class: text-center hero-slide
drawings:
  persist: false
transition: slide-left
mdc: true
duration: 10min
fonts:
  sans: 'Inter'
  serif: 'Inter'
  mono: 'Fira Code'
css: unocss
---

<div class="hero-background"></div>

<div class="hero-content">
  <h1 class="hero-title">The Engine & the Chassis</h1>
  <h2 class="hero-subtitle">How We Talk to AI Today</h2>
  <p class="hero-description">LLM = Engine · Agentic Tool = Chassis</p>
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

.hero-content { margin-top: 7rem; position: relative; z-index: 1; }

.hero-title {
  font-family: 'Inter', sans-serif; font-size: 4rem; font-weight: 800;
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
  <div class="text-4xl mb-2">🚗</div>
  <div class="text-xl font-bold mb-2">The Standard Interface</div>
  <div class="text-sm opacity-75">Agentic tools today</div>
  <div class="text-xs opacity-50 mt-1">4 minutes</div>
</div>

<div v-click>
  <div class="text-4xl mb-2">🧩</div>
  <div class="text-xl font-bold mb-2">Two Concepts to Know</div>
  <div class="text-sm opacity-75">MCP servers & Agent Skills</div>
  <div class="text-xs opacity-50 mt-1">4 minutes</div>
</div>

<div v-click>
  <div class="text-4xl mb-2">⌨️</div>
  <div class="text-xl font-bold mb-2">opencode in action</div>
  <div class="text-sm opacity-75">Live demo</div>
  <div class="text-xs opacity-50 mt-1">2 minutes</div>
</div>

</div>

---
layout: section
---

# Part 1: The Standard Interface

Agentic tools are now the standard way to talk to an LLM

---

# The Engine & the Chassis

<div class="grid grid-cols-2 gap-8 mt-6">

<div v-click class="term-card term-card-green">
  <div class="term-icon">🔧</div>
  <h3 class="term-title">Engine = the LLM</h3>
  <p class="term-desc">The model itself — raw intelligence and language understanding. It generates answers, writes code, reasons, translates.</p>
  <p class="term-desc mt-2">Examples: <strong>Claude 4</strong>, GPT-4o, Mistral Large, Llama 3…</p>
  <p class="term-desc mt-2 opacity-60 text-xs italic">You don't drive a bare engine.</p>
</div>

<div v-click class="term-card term-card-blue">
  <div class="term-icon">🚗</div>
  <h3 class="term-title">Chassis = the Agentic Tool</h3>
  <p class="term-desc">The layer that makes the engine usable — connects it to files, tools, context, memory, and your workflow.</p>
  <p class="term-desc mt-2">It reads files, runs commands, browses the web, and iterates.</p>
  <p class="term-desc mt-2 opacity-60 text-xs italic">It transforms raw power into a drivable experience.</p>
</div>

</div>

<style>
.term-card {
  border-radius: 8px; padding: 1.2rem;
  display: flex; flex-direction: column; gap: 0.5rem;
  border-left: 4px solid;
}
.term-card-green { border-color: #009c6d; background: rgba(0, 156, 109, 0.06); }
.term-card-blue { border-color: #2563eb; background: rgba(37, 99, 235, 0.06); }
.term-icon { font-size: 2rem; }
.term-title { font-size: 1.1rem; font-weight: 700; margin: 0; }
.term-desc { font-size: 0.8rem; line-height: 1.5; opacity: 0.9; }
</style>

---

# Landscape Overview

<div class="grid grid-cols-3 gap-3 mt-4">

<div v-click class="tool-card">
  <div class="tool-logo">🤖</div>
  <div class="tool-name">Claude Code<br/><span class="tool-evolution">→ Claude Cowork</span></div>
  <div class="tool-maker">Anthropic</div>
  <div class="tool-note">The first. Cowork born when non-devs started using it — packaged for teams & entities.</div>
  <div class="avail-badge avail-orange">🔄 négociation en cours</div>
</div>

<div v-click class="tool-card">
  <div class="tool-logo">🧠</div>
  <div class="tool-name">Codex</div>
  <div class="tool-maker">OpenAI</div>
  <div class="tool-note">Unified CLI + open-source option — two strong bets.</div>
  <div class="avail-badge avail-gray">✗ not available</div>
</div>

<div v-click class="tool-card">
  <div class="tool-logo">🌊</div>
  <div class="tool-name">Mistral Vibe</div>
  <div class="tool-maker">Mistral</div>
  <div class="tool-note">Our strategic partner's agentic tool.</div>
  <div class="avail-badge avail-green">✓ available</div>
</div>

<div v-click class="tool-card">
  <div class="tool-logo">🏢</div>
  <div class="tool-name">IBM Bob</div>
  <div class="tool-maker">IBM</div>
  <div class="tool-note">Experimentation currently underway internally.</div>
  <div class="avail-badge avail-orange">🧪 expérimentation en cours</div>
</div>

<div v-click class="tool-card tool-card-highlight">
  <div class="tool-logo">⚙️</div>
  <div class="tool-name">opencode</div>
  <div class="tool-maker">Open source</div>
  <div class="tool-note">Most popular open-source option. Huge ecosystem.</div>
  <div class="avail-badge avail-green">✓ available</div>
</div>

<div v-click class="tool-card tool-card-more">
  <div class="tool-logo">➕</div>
  <div class="tool-name">And many more…</div>
  <div class="tool-maker">Community & Big Tech</div>
  <div class="tool-note">Gemini CLI (Google), Continue (VS Code), OpenClaude, Amp, Cline, Cursor, Windsurf…</div>
  <div class="avail-badge avail-gray">ecosystem growing fast</div>
</div>

</div>

<style>
.tool-card {
  border: 2px solid rgba(141, 201, 171, 0.4);
  border-radius: 8px; padding: 0.7rem 0.6rem;
  text-align: center;
  display: flex; flex-direction: column; align-items: center; gap: 0.35rem;
  background: rgba(141, 201, 171, 0.04);
}
.tool-card-highlight {
  border-color: #009c6d;
  background: rgba(0, 156, 109, 0.08);
}
.tool-card-more {
  border-color: rgba(100, 116, 139, 0.4);
  background: rgba(100, 116, 139, 0.04);
  border-style: dashed;
}
.tool-logo { font-size: 1.6rem; line-height: 1; }
.tool-name { font-size: 0.78rem; font-weight: 700; line-height: 1.3; }
.tool-evolution { font-size: 0.65rem; font-weight: 400; opacity: 0.7; }
.tool-maker { font-size: 0.65rem; opacity: 0.55; }
.tool-note { font-size: 0.65rem; opacity: 0.8; line-height: 1.35; flex: 1; }
.avail-badge {
  font-size: 0.62rem; font-weight: 700; padding: 0.15rem 0.5rem;
  border-radius: 9999px; white-space: nowrap; margin-top: auto;
}
.avail-green { background: rgba(0, 156, 109, 0.15); color: #009c6d; }
.avail-gray { background: rgba(100, 116, 139, 0.15); color: #64748b; }
.avail-orange { background: rgba(217, 119, 6, 0.15); color: #d97706; }
</style>

---

# The Limiting Factor

<div class="mt-8 max-w-3xl mx-auto">

<div class="warning-card">
  <div class="warning-icon">⚠️</div>
  <div class="warning-body">
    <div class="warning-title">A great chassis can't compensate for a weak engine</div>
    <div class="warning-text">
      The <strong>underlying LLM remains the limiting factor</strong>. Whichever agentic tool you use, the quality of its output depends on the model it runs on — its reasoning, its knowledge, its ability to follow instructions.
    </div>
  </div>
</div>

<div v-click class="grid grid-cols-2 gap-6 mt-6">
  <div class="factor-card factor-card-green">
    <div class="factor-title">🚗 Chassis are now nearly feature-equivalent</div>
    <ul class="factor-list">
      <li>All major tools read files, run commands, use MCP</li>
      <li>The real differentiator: <strong>open source vs. closed source</strong></li>
      <li>And <strong>popularity</strong> — community, plugins, integrations</li>
      <li>Some vendors use the chassis for <strong>post-training</strong> (fine-tuning on real agentic tasks) — a growing edge</li>
    </ul>
  </div>
  <div class="factor-card factor-card-orange">
    <div class="factor-title">⚠️ The engine gap: frontier vs. small models</div>
    <ul class="factor-list">
      <li><strong>Frontier models</strong> — Claude Opus/Sonnet, GPT-5, Kimi: deep reasoning, large context, best results</li>
      <li><strong>Small models</strong> — Gemma, Mistral Mini, GPT-OSS: faster & cheaper, but more limited on complex tasks</li>
      <li>Choosing the right model matters as much as the chassis</li>
    </ul>
  </div>
</div>

</div>

<style>
.warning-card {
  display: flex; align-items: flex-start; gap: 1rem;
  background: rgba(217, 119, 6, 0.1);
  border-left: 4px solid #d97706;
  border-radius: 8px; padding: 1.2rem 1.4rem;
}
.warning-icon { font-size: 2rem; flex-shrink: 0; }
.warning-title { font-size: 1rem; font-weight: 700; margin-bottom: 0.4rem; }
.warning-text { font-size: 0.82rem; line-height: 1.55; opacity: 0.9; }
.factor-card {
  border-radius: 8px; padding: 0.9rem 1rem;
  border-left: 3px solid;
}
.factor-card-green { border-color: #009c6d; background: rgba(0, 156, 109, 0.06); }
.factor-card-orange { border-color: #d97706; background: rgba(217, 119, 6, 0.06); }
.factor-title { font-size: 0.8rem; font-weight: 700; margin-bottom: 0.5rem; }
.factor-list { font-size: 0.75rem; padding-left: 1.1rem; line-height: 1.7; opacity: 0.85; }
</style>

---
layout: section
---

# Part 2: Two Concepts to Know

MCP Servers & Agent Skills

---

# Two Open Standards

<div class="aaif-banner">
  <span class="aaif-origin">Born at <strong>Anthropic</strong></span>
  <span class="aaif-arrow">→</span>
  <span class="aaif-dest">Now open standards under <strong>Linux Foundation — Agentic AI Foundation (AAIF)</strong></span>
  <span class="aaif-badge">works with any LLM tool</span>
</div>

<div class="grid grid-cols-2 gap-8 mt-6">

<div v-click class="std-card std-card-green">
  <div class="std-icon">🔌</div>
  <h3 class="std-title">MCP Servers</h3>
  <p class="std-desc"><strong>Model Context Protocol</strong> — a universal adapter that plugs AI into your tools and data: databases, SaaS platforms, APIs, browsers…</p>
  <p class="std-tagline">"Instead of copy-pasting, AI talks directly to your tools."</p>
</div>

<div v-click class="std-card std-card-purple">
  <div class="std-icon">📋</div>
  <h3 class="std-title">Agent Skills</h3>
  <p class="std-desc">A reusable instruction sheet that teaches the AI a repeatable task — packaged once, available to everyone in your team.</p>
  <p class="std-tagline">"Write the recipe once. Anyone can cook."</p>
</div>

</div>

<style>
.aaif-banner {
  display: flex; align-items: center; gap: 0.7rem; flex-wrap: wrap;
  background: rgba(167, 139, 250, 0.1);
  border: 1px solid rgba(167, 139, 250, 0.35);
  border-radius: 8px; padding: 0.6rem 1rem;
  font-size: 0.78rem;
}
.aaif-origin { opacity: 0.75; }
.aaif-arrow { color: #7c3aed; font-weight: 700; }
.aaif-dest { flex: 1; }
.aaif-badge {
  background: rgba(167, 139, 250, 0.15); color: #7c3aed;
  border: 1px solid rgba(167, 139, 250, 0.4);
  padding: 0.15rem 0.6rem; border-radius: 9999px;
  font-size: 0.65rem; font-weight: 700; white-space: nowrap;
}
.std-card {
  border-radius: 8px; padding: 1.2rem;
  display: flex; flex-direction: column; gap: 0.6rem;
  border-left: 4px solid;
}
.std-card-green { border-color: #009c6d; background: rgba(0, 156, 109, 0.06); }
.std-card-purple { border-color: #7c3aed; background: rgba(124, 58, 237, 0.06); }
.std-icon { font-size: 2rem; }
.std-title { font-size: 1.05rem; font-weight: 700; margin: 0; }
.std-desc { font-size: 0.78rem; line-height: 1.5; opacity: 0.9; }
.std-tagline { font-size: 0.72rem; font-style: italic; opacity: 0.65; border-top: 1px solid rgba(0,0,0,0.08); padding-top: 0.5rem; }
</style>

---

# MCP Servers — Concrete Examples

<div class="grid grid-cols-2 gap-8 mt-4">

<div>

### What it looks like in practice

<div v-click class="mcp-example">
  <span class="mcp-server">🗄️ Postgres</span>
  <span class="mcp-prompt">"How many users were created last month?"</span>
</div>

<div v-click class="mcp-example">
  <span class="mcp-server">📚 Context7</span>
  <span class="mcp-prompt">"Migrate this app using the official Angular 20 docs"</span>
</div>

<div v-click class="mcp-example">
  <span class="mcp-server">☁️ IBM Cloud</span>
  <span class="mcp-prompt">"Deploy the latest version to our UAT account"</span>
</div>

<div v-click class="mcp-example">
  <span class="mcp-server">📋 JIRA</span>
  <span class="mcp-prompt">"Create a bug ticket for this issue"</span>
</div>

<div v-click class="mcp-example">
  <span class="mcp-server">🌐 Chrome Dev Tools</span>
  <span class="mcp-prompt">"Improve the design of this page"</span>
</div>

</div>

<div v-click>

### The USB port of AI Agents

<div class="mcp-ecosystem mt-2">
  <div class="mcp-eco-title">Ecosystem</div>
  <div class="mcp-eco-cats">
    <span class="eco-tag">🗄️ Databases</span>
    <span class="eco-tag">☁️ Cloud</span>
    <span class="eco-tag">📊 SaaS</span>
    <span class="eco-tag">📖 Docs</span>
    <span class="eco-tag">🔧 Dev tools</span>
  </div>
  <div class="mcp-eco-note">Hundreds of community servers available</div>
</div>

</div>

</div>

<style>
.mcp-example {
  display: flex; align-items: baseline; gap: 0.6rem;
  padding: 0.5rem 0.7rem; margin-bottom: 0.5rem;
  background: rgba(0, 156, 109, 0.07);
  border-left: 3px solid #009c6d;
  border-radius: 4px;
}
.mcp-server {
  font-size: 0.72rem; font-weight: 700; white-space: nowrap;
  min-width: 90px;
}
.mcp-prompt {
  font-size: 0.75rem; opacity: 0.85; font-style: italic; line-height: 1.3;
}
.teaching-point {
  background: rgba(0, 156, 109, 0.1);
  border-left: 3px solid #009c6d;
  padding: 0.7rem 0.9rem;
  border-radius: 4px;
  font-size: 0.78rem;
  line-height: 1.55;
}
.mcp-ecosystem {
  background: rgba(141, 201, 171, 0.08);
  border: 1px solid rgba(141, 201, 171, 0.3);
  border-radius: 8px; padding: 0.8rem 1rem;
}
.mcp-eco-title { font-size: 0.75rem; font-weight: 700; margin-bottom: 0.5rem; }
.mcp-eco-cats { display: flex; flex-wrap: wrap; gap: 0.4rem; margin-bottom: 0.5rem; }
.eco-tag {
  background: rgba(0, 156, 109, 0.12); color: #009c6d;
  padding: 0.15rem 0.5rem; border-radius: 9999px;
  font-size: 0.68rem; font-weight: 600;
}
.mcp-eco-note { font-size: 0.68rem; opacity: 0.6; font-style: italic; }
</style>

---

# Agent Skills — Concrete Examples

<div class="grid grid-cols-2 gap-8 mt-4">

<div>

### What it looks like in practice

<div v-click class="skill-example">
  <div class="skill-icon">📄</div>
  <div class="skill-body">
    <div class="skill-name">Document creation</div>
    <div class="skill-prompt">"Generate a project summary presentation" → PowerPoint following company template, with standard cover page, logo, and formatting.</div>
  </div>
</div>

<div v-click class="skill-example">
  <div class="skill-icon">🎨</div>
  <div class="skill-body">
    <div class="skill-name">Brand voice</div>
    <div class="skill-prompt">"Write a client email about the delay" → Drafted in the company tone, with correct sign-off, disclaimers, and style.</div>
  </div>
</div>

<div v-click class="skill-example">
  <div class="skill-icon">📐</div>
  <div class="skill-body">
    <div class="skill-name">Application templating</div>
    <div class="skill-prompt">"Bootstrap a new microservice" → Generates the full project structure following company standards: architecture, naming, CI config, README.</div>
  </div>
</div>

</div>

<div v-click>

### The key idea

<div class="teaching-point mt-2">
  📋 Write the recipe once.<br/>
  Anyone can cook — <strong>no technical skills needed</strong>.
</div>

<div class="skill-community mt-4">
  <div class="skill-com-title">Skills are shareable</div>
  <div class="skill-com-text">
    A skill built by one team can be packaged and reused across the organization — or published to the community skills marketplace.
  </div>
</div>

</div>

</div>

<style>
.skill-example {
  display: flex; align-items: flex-start; gap: 0.7rem;
  padding: 0.6rem 0.7rem; margin-bottom: 0.5rem;
  background: rgba(124, 58, 237, 0.06);
  border-left: 3px solid #7c3aed;
  border-radius: 4px;
}
.skill-icon { font-size: 1.3rem; flex-shrink: 0; line-height: 1.4; }
.skill-name { font-size: 0.75rem; font-weight: 700; margin-bottom: 0.2rem; }
.skill-prompt { font-size: 0.72rem; opacity: 0.82; font-style: italic; line-height: 1.35; }
.teaching-point {
  background: rgba(124, 58, 237, 0.08);
  border-left: 3px solid #7c3aed;
  padding: 0.7rem 0.9rem;
  border-radius: 4px;
  font-size: 0.78rem;
  line-height: 1.55;
}
.skill-community {
  background: rgba(124, 58, 237, 0.06);
  border: 1px solid rgba(124, 58, 237, 0.25);
  border-radius: 8px; padding: 0.8rem 1rem;
}
.skill-com-title { font-size: 0.75rem; font-weight: 700; margin-bottom: 0.4rem; }
.skill-com-text { font-size: 0.72rem; opacity: 0.82; line-height: 1.45; }
</style>

---
layout: section
---

# Part 3: opencode in action

Live demo

---

<!-- TEMPLATE SLIDE 1 — à compléter par l'orateur -->

# opencode — Demo

<div class="demo-placeholder">

<div class="demo-header">
  <span class="demo-badge">⌨️ opencode</span>
  <span class="demo-label"><!-- titre du scénario de démo --></span>
</div>

<div class="demo-body">

<!-- Ajouter ici le contenu de la démo :
  - capture d'écran
  - étapes / narration
  - commandes utilisées
-->

<div class="demo-empty">
  <div class="text-4xl mb-4">🎬</div>
  <div class="text-lg font-semibold">Demo content coming here</div>
  <div class="text-sm opacity-60 mt-2">Replace this block with screenshots, steps, or a live walkthrough</div>
</div>

</div>

</div>

<style>
.demo-placeholder {
  border: 2px dashed rgba(0, 156, 109, 0.4);
  border-radius: 12px;
  padding: 1.5rem;
  margin-top: 1rem;
  min-height: 320px;
  display: flex; flex-direction: column; gap: 1rem;
}
.demo-header {
  display: flex; align-items: center; gap: 0.8rem;
  padding-bottom: 0.8rem;
  border-bottom: 1px solid rgba(0, 156, 109, 0.2);
}
.demo-badge {
  background: rgba(0, 156, 109, 0.15); color: #009c6d;
  padding: 0.2rem 0.7rem; border-radius: 9999px;
  font-size: 0.75rem; font-weight: 700;
}
.demo-label {
  font-size: 0.85rem; font-weight: 600; opacity: 0.6;
  font-style: italic;
}
.demo-body { flex: 1; display: flex; align-items: center; justify-content: center; }
.demo-empty { text-align: center; opacity: 0.4; }
</style>

---
<!-- TEMPLATE SLIDE 2 — à compléter par l'orateur (optionnel) -->

# opencode — Second Example

<div class="demo-placeholder">

<div class="demo-header">
  <span class="demo-badge">⌨️ opencode</span>
  <span class="demo-label"><!-- titre du 2ᵉ scénario --></span>
</div>

<div class="demo-body">

<!-- Contenu à ajouter -->

<div class="demo-empty">
  <div class="text-4xl mb-4">🎬</div>
  <div class="text-lg font-semibold">Demo content coming here</div>
  <div class="text-sm opacity-60 mt-2">Replace this block with your second demo scenario</div>
</div>

</div>

</div>

<style>
.demo-placeholder {
  border: 2px dashed rgba(0, 156, 109, 0.4);
  border-radius: 12px;
  padding: 1.5rem;
  margin-top: 1rem;
  min-height: 320px;
  display: flex; flex-direction: column; gap: 1rem;
}
.demo-header {
  display: flex; align-items: center; gap: 0.8rem;
  padding-bottom: 0.8rem;
  border-bottom: 1px solid rgba(0, 156, 109, 0.2);
}
.demo-badge {
  background: rgba(0, 156, 109, 0.15); color: #009c6d;
  padding: 0.2rem 0.7rem; border-radius: 9999px;
  font-size: 0.75rem; font-weight: 700;
}
.demo-label {
  font-size: 0.85rem; font-weight: 600; opacity: 0.6;
  font-style: italic;
}
.demo-body { flex: 1; display: flex; align-items: center; justify-content: center; }
.demo-empty { text-align: center; opacity: 0.4; }
</style>

---
layout: center
class: text-center
---

# Questions?

<div class="mt-8 text-lg opacity-75">
  This presentation was built WITH Claude Code
</div>

<div class="grid grid-cols-3 gap-8 max-w-2xl mx-auto mt-10">

<div>
  <div class="text-3xl mb-2">📧</div>
  <div class="text-sm">Email</div>
</div>

<div>
  <div class="text-3xl mb-2">💬</div>
  <div class="text-sm">Chat</div>
</div>

<div>
  <div class="text-3xl mb-2">🔗</div>
  <div class="text-sm">Links</div>
</div>

</div>

---
layout: center
class: text-center
---

# Thank You!

<div class="mt-8 text-4xl">
🔧 + 🚗 = 🚀
</div>

<PoweredBySlidev mt-10 />

<!-- Global styles for all slides -->
<style global>
html, body, #app, #page-root {
  background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%) !important;
}

body::after {
  content: '';
  position: fixed;
  top: 0; left: 0; right: 0; bottom: 0;
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
