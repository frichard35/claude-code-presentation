# Claude Code Experience Sharing Presentation

## Project Overview
A 20-minute presentation about Claude Code, built WITH Claude Code (meta!), for sharing experience feedback at the company.

**Target Audience**: Company colleagues
**Duration**: ~20 minutes
**Language**: English (all content, code, and interfaces)
**Format**: Offline HTML presentation with embedded local MP4 videos

## Technical Stack
- **Primary**: Slidev (Vue-based, markdown slides)
- **Fallback**: reveal.js (if video issues with Slidev)
- **Deployment**: Local file (no server required)
- **Videos**: Local MP4 files embedded

## Presentation Outline

### Section 1: History of AI Coding Tools (2 min)
- ChatGPT era: Disconnected from IDE, copy-paste workflow
- GitHub Copilot era: IDE integration, autocomplete-style assistance
- Agentic coding era: Multi-file editing, command execution, codebase analysis, active iteration

### Section 2: Claude Code Deep Dive (12 min) - VIDEO HEAVY
Key features to demonstrate:
- **Memory files**: .claudeignore, CLAUDE.md, project context management
- **3 modes**: Default, Accept edits on, Plan mode on
- **Context management**: Token usage, file selection strategies
- **Micro-iterations workflow**:
  1. Gather context
  2. Modify code
  3. Surface checks (linting)
  4. Test/verify
  5. Loop back
- **MCP modules**: Model Context Protocol integrations

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
- ✅ Video embedding tested and working
- ✅ Custom theme applied

### Phase 2: Content Creation ✅ COMPLETED
- ✅ Created 30+ slides following outline
- ✅ Added video placeholders (5 videos)
- ✅ Structured content for 20-minute delivery

### Phase 3: Visual Polish ✅ COMPLETED
- ✅ Animations and transitions added (v-click)
- ✅ Workflow diagrams created (Mermaid)
- ✅ Custom styling for cards and layouts
- ✅ Video integration ready

### Phase 4: Build & Test ✅ COMPLETED
- ✅ Built to SPA format successfully
- ✅ Offline functionality verified
- ✅ Ready for browser testing
- ⏳ Waiting for actual video files

## Next Steps

1. **Record Demo Videos** (5 videos needed):
   - `demo-memory-files.mp4` - CLAUDE.md and .claudeignore demo
   - `demo-modes.mp4` - Mode switching demonstration
   - `demo-context.mp4` - Context management example
   - `demo-iterations.mp4` - Micro-iterations in action
   - `demo-mcp.mp4` - MCP modules showcase

2. **Replace Placeholder Videos**:
   - Copy your recorded MP4 files to `claude-code-presentation/public/videos/`
   - Recommended specs: 1920x1080 or 1280x720, H.264 MP4, 30-60 seconds each

3. **Rebuild for Final Version**:
   ```bash
   npm run build
   ```

4. **Test the Presentation**:
   - Open `dist/index.html` in your browser
   - Test all videos play correctly
   - Practice the timing (~20 minutes)
   - Verify offline functionality

5. **Customize if Needed**:
   - Edit `slides.md` to adjust content
   - Update personal details in Q&A slide
   - Run `npm run dev` for live preview while editing

## Design Principles
- **KISS**: Keep it simple and focused
- **Modern & dynamic**: Animated transitions, engaging visuals
- **Professional**: Company-ready presentation quality
- **Self-contained**: Works 100% offline

## Videos to Create
List of demo videos needed (to be determined during implementation):
- [ ] Claude Code basic workflow
- [ ] Memory files in action
- [ ] Mode switching demonstration
- [ ] Context management example
- [ ] Micro-iterations in practice
- [ ] MCP modules showcase
