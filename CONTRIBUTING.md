# Contributing to Minerva

Guidelines for adding and editing educational content.

---

## 📂 File Organization

### Folder Structure

```
years/
├── 1.g/                    # First year (Støddfrøði C)
│   ├── index.qmd           # Year overview page
│   ├── funktionir/         # Topic: Functions
│   │   ├── index.qmd       # Topic overview (optional)
│   │   ├── lesson_1.qmd
│   │   └── lesson_2.qmd
│   ├── geometri/           # Topic: Geometry
│   └── ...
└── 2.g/                    # Second year (Støddfrøði B)
    └── ...
```

### File Naming

- Use **lowercase** with **underscores**: `my_lesson_name.qmd`
- Keep names **short but descriptive**
- Include topic prefix if helpful: `exp_funk_halveringstid.qmd`

---

## 📝 Creating a New Lesson

### 1. Create the File

Create a `.qmd` file in the appropriate topic folder:

```
years/1.g/funktionir/new_lesson.qmd
```

### 2. Add Frontmatter

Every lesson needs this YAML header:

```yaml
---
title: "Lesson Title in Faroese"
sidebar: sidebar-1g       # Use sidebar-1g for 1.g, sidebar-2g for 2.g
---
```

Optional frontmatter:

```yaml
---
title: "Lesson Title"
sidebar: sidebar-1g
subtitle: "Optional subtitle"
date: 2024-01-15
description: "Brief description for search"
---
```

### 3. Write Content

Use standard Markdown plus Quarto features:

```markdown
# Section Heading

Body text here.

## Subsection

More content...
```

### 4. Add to Sidebar

Edit `_quarto.yml` and add the lesson under the appropriate section:

```yaml
sidebar:
  - id: sidebar-1g
    contents:
      - section: "📚 Funktionir"
        contents:
          - years/1.g/funktionir/existing_lesson.qmd
          - years/1.g/funktionir/new_lesson.qmd    # Add here
```

### 5. Preview and Verify

```bash
quarto preview
```

Check that:
- Lesson appears in sidebar
- All math renders correctly
- Videos load properly
- Links work

---

## 🔢 Math Notation

### Inline Math

Use single dollar signs:

```markdown
The quadratic formula is $x = \frac{-b \pm \sqrt{b^2-4ac}}{2a}$.
```

### Display Math

Use double dollar signs:

```markdown
$$
\int_0^\infty e^{-x^2} dx = \frac{\sqrt{\pi}}{2}
$$
```

### Multi-line Equations

Use the `aligned` environment:

```markdown
$$
\begin{aligned}
  y &= mx + b \\
  y - y_1 &= m(x - x_1)
\end{aligned}
$$
```

### Common Faroese Math Terms

| English | Faroese |
|---------|---------|
| Function | Funktiónur |
| Equation | Likning |
| Graph | Graf |
| Slope | Halling |
| Derivative | Differentialkvotient |

---

## 🎬 Embedding Videos

### YouTube Videos

Use the Quarto video shortcode:

```markdown
{{< video https://www.youtube.com/watch?v=dQw4w9WgXcQ >}}
```

With custom aspect ratio:

```markdown
{{< video https://www.youtube.com/watch?v=dQw4w9WgXcQ aspect-ratio="16x9" >}}
```

### Tips

- Keep videos **short** (5-10 minutes ideal)
- Test that the video ID is correct
- Consider adding a brief text summary below the video

---

## 🖼️ Adding Images

### Local Images

Place images in the `images/` folder or a subfolder:

```
images/
├── 1g/
│   └── funktionir/
│       └── graph_example.png
└── 2g/
```

Reference in your lesson:

```markdown
![Graph description](../../../images/1g/funktionir/graph_example.png)
```

### Best Practices

- Use **PNG** for diagrams, **JPG** for photos
- Keep file sizes **under 500KB**
- Always include **alt text** for accessibility

---

## 📦 Callout Boxes

Quarto provides styled callout blocks:

### Note

```markdown
::: {.callout-note}
This is a helpful note.
:::
```

### Tip

```markdown
::: {.callout-tip}
## Pro Tip
A useful hint for students.
:::
```

### Warning

```markdown
::: {.callout-warning}
Watch out for this common mistake!
:::
```

### Important

```markdown
::: {.callout-important}
Critical information here.
:::
```

---

## ✅ Pre-Commit Checklist

Before committing changes:

- [ ] Frontmatter includes `title` and `sidebar`
- [ ] Lesson added to `_quarto.yml` sidebar
- [ ] Math renders correctly in preview
- [ ] Videos load and play
- [ ] All links work
- [ ] Spelling checked (especially Faroese)
- [ ] `quarto render` completes without errors

---

## 🔄 Workflow Summary

1. **Create** `.qmd` file in correct folder
2. **Add** frontmatter with title and sidebar
3. **Write** content with math and media
4. **Register** in `_quarto.yml` sidebar
5. **Preview** with `quarto preview`
6. **Render** with `quarto render`
7. **Commit** and push to GitHub
