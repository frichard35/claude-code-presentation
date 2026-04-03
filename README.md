# Claude Code Presentations

Two presentations about Claude Code, built WITH Claude Code (meta!).

## Presentations

### 1. `slides.md` — Productivity Boost or Tech Debt Factory? (20 min)

An introductory presentation covering:
- **History of AI Coding Tools** (2 min) - Evolution from ChatGPT to agentic coding
- **Claude Code Deep Dive** (12 min) - Features, modes, context management, workflow
- **Strengths & Weaknesses** (3 min) - Honest assessment
- **Personal Opinion** (3 min) - Lessons learned from real usage

```bash
npm run dev    # dev server → http://localhost:3030
npm run build  # build to dist/
```

### 2. `slides-advanced.md` — Under the Hood (25 min)

An advanced presentation covering:
- **LLM Communication** (8 min) - Stateless requests, tool use & token growth (JSON walkthrough)
- **Anthropic Innovations** (6 min) - Programmatic tool calling, dynamic filtering, tool search, input examples, LSP
- **Ecosystem Terminology** (12 min) - Tools, commands, hooks, MCP servers, skills, agents, plugins/marketplace

```bash
npm run dev2    # dev server → http://localhost:3030
npm run build2  # build to dist/
```

## Quick Start

```bash
npm install
npm run dev   # or dev2 for the advanced presentation
```

## 🖼️ Visual Content

**Note**: Videos have been removed from presentation 1 due to potential lag issues for live/remote audiences. Instead, it features an **image carousel** at the beginning with 46 screenshots.

Images are stored in `public/carousel1/` (high-quality JPG). Navigate with arrow keys or presentation remote.

## Project Structure

```
slides.md               # Presentation 1
slides-advanced.md      # Presentation 2
public/
  carousel1/            # 47 screenshots for the image carousel
  images/               # Context management screenshot
styles/
  custom.css
  index.css
french_spec.txt         # Spec used to build presentation 1
french_spec_advanced.txt # Spec used to build presentation 2
```

## 📊 Presentation 1 Structure

```
slides.md
├── Title & Agenda
├── Part 1: History (3 slides)
│   └── Three eras: ChatGPT → Copilot → Agentic
├── Part 2: Claude Code (12 slides)
│   ├── Memory files (CLAUDE.md with hallucination example)
│   ├── Three modes (Default, Accept Edits, Plan)
│   ├── Context management
│   ├── Micro-iteration workflow
│   └── MCP modules
├── Part 3: Trade-offs (2 slides)
│   ├── Weaknesses
│   └── Strengths
├── Part 4: Opinion (3 slides)
│   └── Key insights & final thoughts
└── Q&A & Thank you
```

## 📊 Presentation 2 Structure

```
slides-advanced.md
├── Title & Agenda
├── Part 1: LLM Communication (4 slides)
│   ├── Turn 1: hello → Hi, how are you?
│   ├── Turn 2: translate → tool_use call
│   └── Turn 3: tool_result → Bienvenue à Cardif
├── Part 2: Innovations (4 slides)
│   ├── Overview (5 cards)
│   ├── Token savings (programmatic, filtering, tool search)
│   └── Accuracy & navigation (input_examples, LSP)
└── Part 3: Ecosystem (6 slides)
    ├── Tool / Command / Hook
    ├── MCP Servers (6 primitives)
    ├── Skills
    ├── Agents & Sub-agents
    └── Marketplace & Plugins
```

## 🎨 Customization

### Changing Theme
Edit `slides.md` frontmatter:
```yaml
---
theme: seriph  # Try: default, apple-basic, dracula, etc.
---
```

### Editing Content
The entire presentation is in `slides.md` using Markdown with Vue components. Edit directly in your favorite editor.

### Adding Custom Styling
Each slide can have its own `<style>` block for custom CSS.

## 🔧 Keyboard Shortcuts (Presenter Mode)

- `Space` / `→` - Next slide
- `←` - Previous slide
- `o` - Overview mode
- `f` - Fullscreen
- `d` - Dark mode toggle
- `g` - Go to slide (type slide number)

## 📦 What's Included

- ✅ 25+ professionally designed slides
- ✅ High-quality image carousel (46 screenshots)
- ✅ Mermaid diagrams for workflows
- ✅ Custom styled cards and layouts
- ✅ Smooth animations with v-click
- ✅ Hallucination demonstration (crossed-out .claudeignore)
- ✅ Offline-ready build
- ✅ Fully responsive design

## 📝 Editing Tips

1. **Live Preview**: Run `npm run dev` to see changes in real-time
2. **Slide Separator**: Use `---` to create new slides
3. **Layouts**: Use frontmatter like `layout: center` or `layout: section`
4. **Animations**: Use `<v-click>` or `v-click` directive for click animations
5. **Code Blocks**: Supports syntax highlighting for all languages

## 🎬 Presentation Tips

1. **Test offline**: Build and test the `dist/` version before presenting
2. **Backup plan**: Have the dev server running as backup
3. **Timing**: Each section has suggested timing - practice to stay on track
4. **Interactive elements**: Use click animations to reveal the hallucination example
5. **Image carousel**: Navigate through 46 high-quality screenshots at the beginning (slide 2)

## 🐛 Troubleshooting

### Build fails
- Run `npm install` again
- Delete `node_modules` and `package-lock.json`, then reinstall

### Styling looks broken
- Clear browser cache
- Rebuild: `rm -rf dist && npm run build`
- Check console for CSS errors

## 📚 Resources

- [Slidev Documentation](https://sli.dev/)
- [Claude Code Documentation](https://docs.claude.com/claude-code)
- [Mermaid Diagrams](https://mermaid.js.org/)

## 🤝 Credits

Built with:
- [Slidev](https://sli.dev/) - Presentation framework
- [Vue.js](https://vuejs.org/) - Component framework
- [UnoCSS](https://unocss.dev/) - CSS engine
- [Mermaid](https://mermaid.js.org/) - Diagram rendering

**Meta note**: This entire presentation was created using Claude Code, demonstrating the tool being presented!

---

## 📄 License

Feel free to use and modify this presentation for your needs.
