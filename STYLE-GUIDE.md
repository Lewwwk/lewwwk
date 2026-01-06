# lewwwk.com Style Guide

**Modern Minimalist Design - Award-Worthy Edition v2**

## Award-Worthy Differentiators

This design achieves award-worthy status through:

1. **Editorial Drop Cap** - Amber-colored drop caps create a distinctive magazine-quality opening for each post
2. **Warm Amber Accent System** - A cohesive accent color (#d97706) that appears in drop caps, H2 underlines, hover states, HR dividers, and selection highlighting
3. **Animated Hover Interactions** - Post entries reveal amber accent lines on hover; navigation links grow underlines smoothly
4. **Bold Typographic Hierarchy** - Extra-bold (800 weight) titles create immediate visual impact
5. **Generous Whitespace** - Thoughtful spacing creates breathing room and reading comfort

---

## Color Palette

### Light Mode (Default)

| Token | Hex | Usage |
|-------|-----|-------|
| `--theme` | `#ffffff` | Page background |
| `--primary` | `#111111` | Headings, strong text |
| `--secondary` | `#555555` | Meta text, captions |
| `--tertiary` | `#f8f8f8` | Blockquote background |
| `--content` | `#1a1a1a` | Body text |
| `--border` | `#e0e0e0` | Borders, dividers |
| `--code-bg` | `#f5f5f5` | Code block background |
| **Accent** | `#d97706` | Primary accent (amber) |
| **Accent Light** | `#f59e0b` | Secondary accent |

### Dark Mode

| Token | Hex | Usage |
|-------|-----|-------|
| `--theme` | `#0f0f0f` | Page background |
| `--primary` | `#f5f5f5` | Headings |
| `--secondary` | `#9a9a9a` | Meta text |
| `--tertiary` | `#1a1a1a` | Blockquote background |
| `--content` | `#e8e8e8` | Body text |
| `--border` | `#2d2d2d` | Borders |
| **Accent** | `#f59e0b` | Accent (light amber) |

---

## Typography

### Font Stacks

**Body Text (Serif)**
```css
font-family: "Charter", "Bitstream Charter", "Sitka Text", Cambria, Georgia, serif;
```

**Headings (Sans-Serif)**
```css
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
```

**Code**
```css
font-family: ui-monospace, SFMono-Regular, "SF Mono", Menlo, Monaco, Consolas, monospace;
```

### Size Scale

| Element | Desktop | Mobile | Weight |
|---------|---------|--------|--------|
| Hero Title | 4rem | 2.5rem | 800 |
| Post Title | 3rem | 1.85rem | 800 |
| H2 | 1.75rem | 1.35rem | 700 |
| H3 | 1.4rem | 1.15rem | 700 |
| Body | 18px | 17px | 400 |
| Meta | 0.75rem | 0.75rem | 400 |
| Navigation | 0.9rem | 0.8rem | 600 |

### Line Heights
- Body: 1.7
- Headings: 1.08-1.2
- Post list content: 1.6

---

## Layout

- **Max Content Width**: 720px
- **Main Padding**: 0 2rem (desktop), 0 1.25rem (mobile)
- **Post Entry Padding**: 2.5rem 0 (desktop), 1.5rem 0 (mobile)
- **Hero Padding**: 5rem 0 4rem 0 (desktop), 2.5rem 0 2rem 0 (mobile)

---

## Signature Design Elements

### 1. Drop Cap
```css
.post-content > p:first-of-type::first-letter {
  float: left;
  font-family: var(--font-heading);
  font-size: 4rem;
  font-weight: 800;
  line-height: 0.8;
  padding-right: 0.6rem;
  color: var(--accent);
}
```

### 2. H2 with Accent Underline
```css
.post-content h2 {
  font-size: 1.75rem;
  font-weight: 700;
  padding-bottom: 0.5rem;
  border-bottom: 2px solid var(--accent);
  display: inline-block;
}
```

### 3. Post Entry Hover Effect
```css
.post-entry::before {
  content: '';
  position: absolute;
  left: -2rem;
  top: 50%;
  transform: translateY(-50%);
  height: 0;
  width: 4px;
  background: var(--accent);
  transition: height 0.3s ease;
}

.post-entry:hover::before {
  height: 60%;
}

.post-entry:hover .entry-header h2 {
  color: var(--accent);
}
```

### 4. Navigation Animated Underline
```css
nav a::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 0;
  height: 2px;
  background: var(--accent);
  transition: width 0.25s ease;
}

nav a:hover::after {
  width: 100%;
}
```

### 5. Amber Selection
```css
::selection {
  background: var(--accent);
  color: var(--theme);
}
```

---

## Blockquotes
```css
blockquote {
  border-left: 4px solid var(--accent);
  margin: 2.5rem 0;
  padding: 1rem 0 1rem 2rem;
  font-style: italic;
  font-size: 1.15rem;
  color: var(--secondary);
  background: var(--tertiary);
}
```

---

## Horizontal Rules
```css
.post-content hr {
  border: none;
  height: 3px;
  background: linear-gradient(90deg, var(--accent), var(--accent-light));
  margin: 4rem auto;
  width: 60px;
  border-radius: 2px;
}
```

---

## Focus States (Accessibility)
```css
a:focus-visible,
button:focus-visible {
  outline: 2px solid var(--accent);
  outline-offset: 2px;
}
```

---

## File Structure

```
site/
├── assets/css/extended/
│   └── custom.css              # All custom styles (~650 lines)
├── layouts/_default/
│   └── about.html              # Custom about page layout
├── hugo.toml                   # defaultTheme = "light"
├── content/
│   ├── about.md                # No drop cap layout
│   └── posts/                  # 179 blog posts
└── static/images/
    └── recovered/              # 10 recovered images
```

---

## Deployment

```bash
cd site
hugo --minify
wrangler pages deploy public --project-name=lewwwk
```

---

## Design History

- **v1**: Initial migration with PaperMod defaults
- **v2**: Award-worthy redesign with 10 design loops including:
  - Editorial drop caps with amber accent
  - Bold typographic hierarchy (weight 800)
  - Animated hover interactions
  - Refined color palette with warm amber
  - Mobile-first responsive design
  - Custom about page layout
  - Comprehensive accessibility features
