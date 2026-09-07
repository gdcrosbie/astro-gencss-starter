# Project Instructions & Agent Guidelines (GenCSS)

## 1. Project Context & Boundaries

> [!IMPORTANT]
> **This is a standalone Astro project styled with GenCSS / FEWD design tokens.**
> - Do **not** look for or invoke WordPress / Etch builder tools (`etch-connector`, `nibwp-*`, `novamira-*`, `scwp-acss-mcp`).
> - There is no WordPress database, live builder tab, or per-element Etch styles layer here.
> - Component styling belongs inside `.astro` component `<style>` blocks or standard CSS files in `src/styles/`.

---

## 2. Development & Dev Server

When starting the dev server, use background mode:
```bash
astro dev --background
```
Manage the background server with:
- `astro dev status`
- `astro dev logs`
- `astro dev stop`

---

## 3. Styling & CSS Architecture (Astro + GenCSS)

This project consumes **GenCSS / FEWD** design tokens from `src/styles/tokens.css`.

### Core Rules:
- **Token Source**: `src/styles/tokens.css` (imported via `src/styles/global.css`).
- **Methodology**: Strict BEM methodology (`.c-block`, `.c-block__element`, `.c-block--modifier`).
- **No Utility Frameworks**: No Tailwind CSS, no utility-class soup, no inline `style=""` attributes.
- **Component Styling**: Write clean CSS in component `<style>` blocks referencing native GenCSS custom properties.

### Mandatory: CSS Logical Properties
Always author flow-relative logical properties instead of physical dimensions:
- **Padding**: Use `padding-block` and `padding-inline` (never `padding-top/bottom/left/right`).
- **Margins**: Use `margin-block` and `margin-inline` (never `margin-top/bottom/left/right`).
- **Sizing**: Use `max-inline-size`, `inline-size`, `block-size`, `min-block-size` where suitable.
- **Positioning**: Use `inset`, `inset-block-start`, `inset-block-end`, `inset-inline-start`, `inset-inline-end` (never physical `top/bottom/left/right`).
- **Borders & Dividers**: Use `border-block-start`, `border-block-end`, `border-inline-start`, `border-inline-end`.

---

## 4. GenCSS / FEWD Token Architecture & Constraints

Always inspect `src/styles/tokens.css` before using tokens:

### Spacing & Gaps:
- **Spacing Scale**: `--space-xxs`, `--space-xs`, `--space-s`, `--space-m`, `--space-l`, `--space-xl`, `--space-2xl`, `--space-3xl`.
- **Gap Tokens**: `--gap-xs`, `--gap-s`, `--gap-m`, `--gap-l`.
- **Contextual Spacing**: `--gap-content` (varies, default `--space-l`), `--gap-grid` (default `--space-xl`), `--gap-container` (default `--space-2xl`).
- **Padding Aliases**: `--padding-xs` through `--padding-2xl`, `--padding`.
- **Margin Aliases**: `--margin-xs` through `--margin-2xl`, `--margin`.

### Typography:
- **Text Scale**: `--text-xxs`, `--text-xs`, `--text-s`, `--text-m`, `--text-l`, `--text-xl`, `--text-xxl`, `--text-xxxl`.
- **Display & Feature**: `--text-display` (`--text-xxxl`), `--text-feature` (`--text-xxl`).
- **Heading Sizes**: `--h1` (`--text-xl`), `--h2` (`--text-l`), `--h3` (`--text-m`), `--h4` (`--text-s`), `--h5` (`--text-s`), `--h6` (`--text-xs`).
- **Heading Properties**: `--font-heading`, `--weight-heading`, `--leading-heading`, `--tracking-heading`, `--style-heading`.
- **Body Properties**: `--font-body`, `--weight-body`, `--leading-body`, `--tracking-tight`, `--tracking-wide`, `--tracking-wider`.
- **Monospace**: `--font-mono`.

### Colors & Palette:
- **Families**: `--primary`, `--secondary`, `--tertiary`, `--accent`, `--base`, `--neutral`.
- **Shade Step Scale**:
  - `-light-2` (lightest)
  - `-light-1`
  - `[base]` (e.g. `--primary`)
  - `-dark-1`
  - `-dark-2` (darkest)
- **Built-in Transparencies**:
  - `--primary-trans10` through `--primary-trans90` (steps of 10%)
  - `--secondary-trans10` through `--secondary-trans90`
  - `--accent-trans10` through `--accent-trans90`
  - `--white-10` through `--white-90`
  - `--black-10` through `--black-90`
- **Theme Semantic Roles**:
  - `--background` (maps to `--base-dark`)
  - `--surface` (maps to `--base`)
  - `--surface-raised` (maps to `--base-light-1` or `--base-light-2`)
  - `--color` (maps to `--white` on dark mode)
  - `--color-muted` (maps to `--neutral` or `--white-70`)
  - `--border-color` (maps to `--white-10` or `--white-20`)

### Borders, Radius & Shadows:
- **Radius**: `--radius-s`, `--radius-m`, `--radius-l`, `--radius-full` (pill), `--radius-card`, `--radius` (default `--radius-m`).
- **Shadows**: `--shadow-s`, `--shadow-m`, `--shadow-l`, `--shadow-card`, `--shadow-1` through `--shadow-4`.
- **Transitions**: `--transition-fast`, `--transition-base`, `--transition-slow`, `--transition`.

### Layout Primitives:
- **Container**:
  ```css
  inline-size: 100%;
  max-inline-size: var(--container-width, 1200px);
  margin-inline: auto;
  padding-inline: clamp(1rem, 4vw, var(--space-m));
  ```
- **Section Spacing**:
  ```css
  padding-block: var(--section-block, var(--space-xl));
  ```

---

## 5. Documentation References

Consult these guides before working on Astro features:
- [Adding pages, dynamic routes, or middleware](https://docs.astro.build/en/guides/routing/)
- [Working with Astro components](https://docs.astro.build/en/basics/astro-components/)
- [Using framework components](https://docs.astro.build/en/guides/framework-components/)
- [Adding or managing content](https://docs.astro.build/en/guides/content-collections/)
- [Adding styles](https://docs.astro.build/en/guides/styling/)
