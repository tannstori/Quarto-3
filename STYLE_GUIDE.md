# Minerva Style Guide

Design standards and formatting conventions.

---

## 🎨 Design Philosophy

**Calm, Academic, Readable**

Minerva uses a clean, distraction-free design optimized for:
- Extended reading sessions
- Mathematical content clarity
- Mobile and desktop viewing

---

## 🎯 Theme & Colors

### Base Theme

**Bootswatch Flatly** — A professional, calm theme with excellent contrast.

### Color Palette

| Role | Color | Hex | Usage |
|------|-------|-----|-------|
| Primary | Teal | `#18bc9c` | Links, buttons, accents |
| Secondary | Dark Gray | `#95a5a6` | Muted text, borders |
| Success | Green | `#18bc9c` | Positive indicators |
| Info | Blue | `#3498db` | Information callouts |
| Warning | Orange | `#f39c12` | Warnings, cautions |
| Danger | Red | `#e74c3c` | Errors, important warnings |
| Background | White | `#ffffff` | Main content area |
| Text | Dark | `#2c3e50` | Body text |

### Usage Guidelines

- **Don't** add random colors — stick to the palette
- **Do** use primary color for interactive elements
- **Do** use semantic colors for callouts (info, warning, etc.)

---

## 📝 Typography

### Fonts

| Purpose | Font | Fallback |
|---------|------|----------|
| Body text | Source Sans 3 | system-ui |
| Code | JetBrains Mono | monospace |
| Math | KaTeX default | — |

### Font Sizes

- Body: 16px base
- H1: 2rem (32px)
- H2: 1.5rem (24px)
- H3: 1.25rem (20px)
- Small: 0.875rem (14px)

### Line Height

- Body: 1.6 (comfortable reading)
- Headings: 1.2 (tighter)

---

## 📐 Layout & Spacing

### Grid Structure

```
┌─────────────────────────────────────────────────────────┐
│                      Navbar                              │
├──────────┬──────────────────────────────────────┬───────┤
│          │                                      │       │
│ Sidebar  │       Main Content                   │  TOC  │
│  280px   │         850px                        │ 220px │
│          │                                      │       │
├──────────┴──────────────────────────────────────┴───────┤
│                      Footer                              │
└─────────────────────────────────────────────────────────┘
```

### Spacing Scale

Use consistent spacing multiples:

- `0.25rem` — Tiny (4px)
- `0.5rem` — Small (8px)
- `1rem` — Base (16px)
- `1.5rem` — Medium (24px)
- `2rem` — Large (32px)
- `3rem` — Extra large (48px)

---

## 🧮 Math Styling

### Inline Math

Rendered inline with text, matching font size.

```markdown
The area is $A = \pi r^2$.
```

### Display Math

Centered, slightly larger, with breathing room.

```markdown
$$
\sum_{i=1}^{n} i = \frac{n(n+1)}{2}
$$
```

### Multi-line Equations

Use `aligned` for step-by-step derivations:

```markdown
$$
\begin{aligned}
  2x + 3 &= 7 \\
  2x &= 4 \\
  x &= 2
\end{aligned}
$$
```

---

## 📦 Callout Styles

The theme provides styled callouts:

### Standard Callouts

| Type | Color | Usage |
|------|-------|-------|
| Note | Blue | General information |
| Tip | Green | Helpful hints |
| Warning | Orange | Cautions, common mistakes |
| Important | Red | Critical information |

### Examples

**Note** — Background information:
```markdown
::: {.callout-note}
This formula was discovered by Euler in 1748.
:::
```

**Tip** — Study advice:
```markdown
::: {.callout-tip}
## Study Tip
Practice this technique with different values.
:::
```

**Warning** — Common mistakes:
```markdown
::: {.callout-warning}
Don't forget to check for division by zero!
:::
```

---

## 🃏 Card Components

### Course Cards (Homepage)

Used on the homepage for year navigation:

```html
<div class="course-cards">
  <a href="years/1.g/index.qmd" class="course-card">
    <div class="card-content">
      <span class="course-icon">📐</span>
      <h3>1.g</h3>
      <p>Støddfrøði C</p>
    </div>
  </a>
</div>
```

### Topic Cards (Year Pages)

Used on year overview pages:

```markdown
::: {.topic-grid}
::: {.topic-card}
### [📊 Funktionir](funktionir/index.qmd)
Linear and exponential functions
:::
:::
```

### Lesson Cards (Topic Pages)

For individual lessons:

```markdown
::: {.lesson-grid}
::: {.lesson-card}
### [Lesson Title](lesson.qmd)
Brief description
:::
:::
```

---

## 📱 Responsive Design

### Breakpoints

| Name | Width | Behavior |
|------|-------|----------|
| Mobile | < 576px | Single column, hidden sidebar |
| Tablet | 576-991px | Collapsible sidebar |
| Desktop | ≥ 992px | Full layout with sidebar |

### Mobile Considerations

- Sidebar auto-collapses on mobile
- TOC moves to top of page
- Cards stack vertically
- Math remains readable

---

## ✅ Style Checklist

When creating content:

- [ ] Use standard Quarto markdown
- [ ] Use callouts for highlighted content
- [ ] Use proper heading hierarchy (H1 → H2 → H3)
- [ ] Keep paragraphs short (3-5 sentences)
- [ ] Test on mobile viewport
- [ ] Avoid inline styles — use existing classes
- [ ] Check math renders at all sizes

---

## 🚫 Avoid

**Don't:**
- Add inline CSS to `.qmd` files
- Create custom colors outside the palette
- Use `<font>` or other deprecated HTML
- Mix heading levels (e.g., H1 → H3)
- Create ultra-wide content that breaks layout

**Do:**
- Use semantic HTML and Quarto classes
- Let the theme handle styling
- Use callouts for emphasis
- Keep content width within bounds
