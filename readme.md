# Minerva — Faroese Mathematics Education

A Quarto-based website for high-school mathematics education in Faroese.

---

## 🎯 Overview

Minerva is an educational platform covering:

- **1.g** — Støddfrøði C (first-year mathematics)
- **2.g** — Støddfrøði B (second-year mathematics)

Built with [Quarto](https://quarto.org) and hosted on GitHub Pages.

---

## 📁 Project Structure

```
quarto_3/
├── _quarto.yml          # Main Quarto configuration
├── index.qmd            # Homepage
├── about.qmd            # About page
├── styles/
│   └── custom.scss      # All custom styling
├── _includes/
│   ├── footer.html      # Site footer
│   ├── navbar-handler.html
│   └── collapse-handler.html
├── years/
│   ├── 1.g/             # First year lessons
│   │   ├── index.qmd
│   │   ├── funktionir/
│   │   ├── geometri/
│   │   └── ...
│   └── 2.g/             # Second year lessons
│       ├── index.qmd
│       ├── differentialrokning/
│       └── ...
├── images/              # Image assets
├── docs/                # Built site (GitHub Pages)
└── legacy/              # Archived old files
```

---

## 🚀 Quick Start

### Prerequisites

1. Install [Quarto](https://quarto.org/docs/get-started/) (v1.3+)
2. A code editor (VS Code recommended)

### Preview Locally

```bash
quarto preview
```

Opens a live-reloading preview at `http://localhost:4567`

### Build for Production

```bash
quarto render
```

Output goes to `docs/` folder.

---

## 📝 Adding Content

### New Lesson

1. Create a `.qmd` file in the appropriate folder:
   ```
   years/1.g/funktionir/my_new_lesson.qmd
   ```

2. Add frontmatter:
   ```yaml
   ---
   title: "Lesson Title"
   sidebar: sidebar-1g
   ---
   ```

3. Add the lesson to `_quarto.yml` sidebar section.

4. Preview and commit.

### Math Notation

Use LaTeX syntax:

- Inline: `$x^2 + y^2 = r^2$`
- Display: `$$\int_0^1 f(x)\,dx$$`

### Video Embeds

Use the shortcode:

```markdown
{{< video https://www.youtube.com/watch?v=VIDEO_ID >}}
```

---

## 🎨 Styling

All styles are in `styles/custom.scss`. The site uses:

- **Theme:** Bootswatch Flatly (calm, academic)
- **Fonts:** Source Sans 3 (text), JetBrains Mono (code)

See [STYLE_GUIDE.md](STYLE_GUIDE.md) for details.

---

## 🌐 Deployment

The site is deployed via GitHub Pages from the `docs/` folder.

See [DEPLOYMENT.md](DEPLOYMENT.md) for full instructions.

---

## 📚 Documentation

| Document | Description |
|----------|-------------|
| [CONTRIBUTING.md](CONTRIBUTING.md) | How to add lessons |
| [STYLE_GUIDE.md](STYLE_GUIDE.md) | Formatting standards |
| [DEPLOYMENT.md](DEPLOYMENT.md) | GitHub Pages setup |

---

## 📄 License

Educational content for Minerva / Faroe Islands.
