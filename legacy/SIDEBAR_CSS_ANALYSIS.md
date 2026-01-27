# Sidebar CSS Analysis & Comparison

## Files Created:

1. **minimal_test.css** (16 lines)
   - ONLY the vertical collapse fix
   - Pure Quarto defaults for everything else

2. **minerva_essentials.css** (115 lines)
   - Essential sidebar styling
   - Critical fixes
   - Clean, maintainable

3. **minerva_theme.css** (1200+ lines)
   - Full custom design
   - All animations, gradients, effects

---

## What Can Be SAFELY REMOVED from Sidebar CSS:

### ✅ CAN REMOVE (Quarto handles these):
```css
/* Width controls - Quarto handles via _quarto.yml */
.sidebar { width: 260px; }

/* Basic display - Quarto default works */
#quarto-sidebar { display: block; }

/* Standard padding - Quarto provides */
.sidebar-item { padding: 0.5rem; }
```

### ⚠️ KEEP (Essential functionality):
```css
/* CRITICAL: Vertical collapse fix */
#quarto-sidebar .sidebar-section.collapse {
  height: auto !important;
  transition: height 0.35s ease !important;
}

/* Active state (important for UX) */
.sidebar-item.active {
  border-left: 3px solid var(--minerva-secondary);
  background: rgba(59, 130, 246, 0.08);
}

/* Nested indentation (readability) */
.sidebar-section .sidebar-item { padding-left: 0.6rem !important; }
.sidebar-section .sidebar-section .sidebar-item { padding-left: 1.2rem !important; }
```

### 🎨 OPTIONAL (Visual polish):
```css
/* These are nice-to-have but not required */
.sidebar { box-shadow: 2px 0 8px rgba(0,0,0,0.05); }
.sidebar-item:hover { transform: translateX(4px); }
.sidebar-title { background: linear-gradient(...); }
```

---

## Recommendation:

**Switch to `minerva_essentials.css`** (the simplified version):
- 90% smaller file
- Same core functionality
- Easier to maintain
- Still looks professional
- Keeps the critical vertical collapse fix

---

## To Test Each Version:

Edit `_quarto.yml` line 21:

```yaml
# Option 1: Pure Quarto (will show horizontal collapse issue)
css: minimal_test.css

# Option 2: Essential only (RECOMMENDED)
css: minerva_essentials.css

# Option 3: Full custom (current)
css: minerva_theme.css
```

Then run: `quarto preview`
