# Claude Code Presentations

## Project Overview
Two Slidev presentations about Claude Code, built WITH Claude Code (meta!), for sharing experience feedback at the company.

**Target Audience**: Company colleagues (live and remote)
**Language**: English (all content, code, and interfaces)
**Format**: Offline HTML presentations (videos removed due to lag concerns)

### Presentation 1 — `slides.md`
**Duration**: ~20 minutes — Introductory, experience sharing
`npm run dev` / `npm run build`

### Presentation 2 — `slides-advanced.md`
**Duration**: ~25 minutes — Advanced, technical deep-dive
`npm run dev2` / `npm run build2`

## Technical Stack
- **Primary**: Slidev v52 (Vue-based, markdown slides)
- **Theme**: seriph + custom green styling (`#009c6d`)
- **Deployment**: Local file (no server required)
- **Visuals**: Image carousel with high-quality screenshots (46 images) in presentation 1

## Presentation Outline

### Section 1: History of AI Coding Tools (2 min)
- ChatGPT era: Disconnected from IDE, copy-paste workflow
- GitHub Copilot era: IDE integration, autocomplete-style assistance
- Agentic coding era: Multi-file editing, command execution, codebase analysis, active iteration

### Section 2: Claude Code Deep Dive (12 min)
Key features to demonstrate:
- **Memory files**: CLAUDE.md for project context (includes hallucination example of .claudeignore)
- **3 modes**: Default, Accept edits on, Plan mode on
- **Context management**: Token usage, file selection strategies
- **Micro-iterations workflow**:
  1. Gather context
  2. Modify code
  3. Surface checks (linting)
  4. Test/verify
  5. Loop back
- **MCP modules**: Model Context Protocol integrations

**Note**: Videos removed. Using image carousel at beginning instead.

### Section 3: Strengths & Weaknesses (3 min)

**Weaknesses:**
- Hallucinations still exist (though iterations help correct)
- Often too enterprising - needs to be reined in for simpler solutions
- Developer risks: becoming lazy/overconfident OR overly ambitious leading to mental overload

**Strengths:**
- Fast implementation speed
- High-quality writing (well-written even if occasionally hallucinated)
- Free code/POCs for validating ideas
- Powerful internet research - less time on Google/Stack Overflow
- Enables more ambitious feature development (watch for tech debt)

### Section 4: Personal Opinion (3 min)
**Disclaimer**: Tested on small codebases

Key insights:
- **Context is central** - often the limiting factor
- Started with "vibe coding" (auto-accept mode) - stopped due to poor internal design despite working externally
- **Tests are crucial** for iteration without excessive token consumption
- Similar to pair programming but non-human - be careful
- Hard to go back once you've started working this way

## Implementation Status

### Phase 1: Project Setup ✅ COMPLETED
- ✅ Slidev project initialized
- ✅ Configured for offline use
- ✅ Custom theme applied

### Phase 2: Content Creation ✅ COMPLETED
- ✅ Created 25+ slides following outline
- ✅ Removed video slides (lag concerns for live/remote audience)
- ✅ Structured content for 20-minute delivery
- ✅ Added hallucination demonstration (crossed-out .claudeignore)

### Phase 3: Visual Polish ✅ COMPLETED
- ✅ Animations and transitions added (v-click)
- ✅ Workflow diagrams created (Mermaid)
- ✅ Custom styling for cards and layouts
- ✅ Red cross-out animation for hallucination example

### Phase 4: Build & Test ✅ COMPLETED
- ✅ Built to SPA format successfully
- ✅ Offline functionality verified
- ✅ Ready for browser testing

### Phase 5: Image Carousel ✅ COMPLETED
- ✅ Created carousel component with 46 high-quality images
- ✅ Integrated at beginning of presentation (slide 2)
- ✅ Native Slidev navigation with keyboard/remote support
- ✅ Images upgraded to higher quality for better visual experience
- ✅ Counter display showing progress (X / 46)

## Next Steps

1. **Test the Presentations**:
   - `npm run dev` / `npm run dev2` for live preview
   - Practice timing (~20 min for slides.md, ~25 min for slides-advanced.md)
   - Test hallucination animation reveals (slides.md)
   - Verify offline functionality after build

2. **Final Polish**:
   - Edit `slides.md` or `slides-advanced.md` as needed
   - Update personal details in Q&A slide
   - Run `npm run build` / `npm run build2` for offline export

## Design Principles
- **KISS**: Keep it simple and focused
- **Modern & dynamic**: Animated transitions, engaging visuals
- **Professional**: Company-ready presentation quality
- **Self-contained**: Works 100% offline
- **No video lag**: Static images instead of videos for remote audiences
