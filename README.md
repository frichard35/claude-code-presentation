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

## 🎥 Adding Your Videos

The presentation includes placeholders for 5 demo videos. Replace the empty placeholder files in `public/videos/` with your actual MP4 recordings:

1. **demo-memory-files.mp4** - Demonstrating CLAUDE.md and .claudeignore usage
2. **demo-modes.mp4** - Switching between Default, Accept Edits, and Plan modes
3. **demo-context.mp4** - Managing context effectively
4. **demo-iterations.mp4** - Watching Claude Code iterate on a feature
5. **demo-mcp.mp4** - Using MCP modules to integrate external tools

### Video Recording Tips

For best results:
- **Resolution**: 1920x1080 or 1280x720
- **Format**: MP4 (H.264 codec)
- **Duration**: 30-60 seconds per video
- **Content**: Screen recordings showing Claude Code in action
- **Audio**: Optional but recommended for narration

You can use tools like:
- macOS: QuickTime Player (Cmd+Ctrl+N for screen recording)
- Windows: Xbox Game Bar (Win+G)
- Cross-platform: OBS Studio

## 📊 Presentation Structure

```
slides.md (30+ slides)
├── Title & Agenda
├── Part 1: History (3 slides)
│   ├── Timeline of AI coding tools
│   └── Three eras: ChatGPT → Copilot → Agentic
├── Part 2: Claude Code (15 slides)
│   ├── Overview & features
│   ├── Memory files (CLAUDE.md, .claudeignore)
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

- ✅ 30+ professionally designed slides
- ✅ Mermaid diagrams for workflows
- ✅ Custom styled cards and layouts
- ✅ Smooth animations with v-click
- ✅ Video embedding support
- ✅ Offline-ready build
- ✅ Fully responsive design

## 📝 Editing Tips

1. **Live Preview**: Run `npm run dev` to see changes in real-time
2. **Slide Separator**: Use `---` to create new slides
3. **Layouts**: Use frontmatter like `layout: center` or `layout: section`
4. **Animations**: Use `<v-click>` or `v-click` directive for click animations
5. **Code Blocks**: Supports syntax highlighting for all languages

## 🎬 Presentation Tips

1. **Practice with videos**: Make sure all videos play correctly
2. **Test offline**: Build and test the `dist/` version before presenting
3. **Backup plan**: Have the dev server running as backup
4. **Timing**: Each section has suggested timing - practice to stay on track
5. **Interactive elements**: Mermaid diagrams and click animations work best in live demo

## 🐛 Troubleshooting

### Videos not playing
- Ensure video files are in `public/videos/`
- Check video codec (should be H.264 MP4)
- Try opening in a different browser

### Build fails
- Run `npm install` again
- Delete `node_modules` and `package-lock.json`, then reinstall
- Check that all video files exist (even if empty)

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
