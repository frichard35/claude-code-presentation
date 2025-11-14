# Claude Code Experience Sharing Presentation

## Project Overview
A 20-minute presentation about Claude Code, built WITH Claude Code (meta!), for sharing experience feedback at the company.

**Target Audience**: Company colleagues (live and remote)
**Duration**: ~20 minutes
**Language**: English (all content, code, and interfaces)
**Format**: Offline HTML presentation (videos removed due to lag concerns)

## Technical Stack
- **Primary**: Slidev (Vue-based, markdown slides)
- **Deployment**: Local file (no server required)
- **Visuals**: Image carousel at beginning (to be implemented)

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

## Next Steps

1. **Add Image Carousel** (To be implemented):
   - Create carousel component at beginning of presentation
   - Add screenshots/images to `public/images/` directory
   - Show Claude Code features visually without video lag
   - Recommended image specs: 1920x1080, PNG/JPG format

2. **Test the Presentation**:
   - Open `dist/index.html` in your browser
   - Practice the timing (~20 minutes)
   - Test hallucination animation reveals
   - Verify offline functionality

3. **Final Polish**:
   - Edit `slides.md` to adjust content as needed
   - Update personal details in Q&A slide
   - Run `npm run dev` for live preview while editing

## Design Principles
- **KISS**: Keep it simple and focused
- **Modern & dynamic**: Animated transitions, engaging visuals
- **Professional**: Company-ready presentation quality
- **Self-contained**: Works 100% offline
- **No video lag**: Static images instead of videos for remote audiences
