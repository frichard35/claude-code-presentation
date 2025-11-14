# Claude Code Experience Feedback Presentation

A comprehensive 20-minute presentation about Claude Code, built WITH Claude Code (meta!).

## 🎯 Overview

This presentation covers:
- **History of AI Coding Tools** (2 min) - Evolution from ChatGPT to agentic coding
- **Claude Code Deep Dive** (12 min) - Features, modes, context management, workflow
- **Strengths & Weaknesses** (3 min) - Honest assessment
- **Personal Opinion** (3 min) - Lessons learned from real usage

## 🚀 Quick Start

### Development Mode
```bash
npm install
npm run dev
```

The presentation will open in your browser at `http://localhost:3030`

### Build for Offline Use
```bash
npm run build
```

The built presentation will be in the `dist/` folder. You can:
- Open `dist/index.html` directly in a browser (works offline)
- Copy the entire `dist/` folder to share
- Host the `dist/` folder on any web server

## 🖼️ Visual Content

**Note**: Videos have been removed from the presentation due to potential lag issues for live/remote audiences. Instead, the presentation will feature an **image carousel** at the beginning to showcase Claude Code features.

### Adding Image Carousel (To Be Implemented)

The image carousel will be added at the start of the presentation to show:
- Screenshots of Claude Code interface
- Key features in action
- Workflow examples
- Context management visuals

Images should be placed in `public/images/` directory (format: PNG/JPG, recommended resolution: 1920x1080).

## 📊 Presentation Structure

```
slides.md (30+ slides)
├── Title & Agenda
├── Part 1: History (3 slides)
│   ├── Timeline of AI coding tools
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
│   ├── Disclaimer
│   ├── Key insights
│   └── Final thoughts
└── Q&A & Thank you
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
- ✅ Mermaid diagrams for workflows
- ✅ Custom styled cards and layouts
- ✅ Smooth animations with v-click
- ✅ Hallucination demonstration (crossed-out .claudeignore)
- ✅ Offline-ready build
- ✅ Fully responsive design
- ⏳ Image carousel (to be implemented)

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
5. **Image carousel**: Will be added at the beginning for visual demonstrations

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
