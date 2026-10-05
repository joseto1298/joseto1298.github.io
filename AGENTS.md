# AGENTS.md

## Repo overview

Static portfolio site — single `index.html`, no framework, no build step, no dependencies. Hosted on GitHub Pages (https://joseto1298.github.io/).

## How to investigate

- `index.html` is the only source of truth for the site content, styles, and SEO metadata.
- `README.md` mirrors the portfolio copy; if content conflicts, `index.html` wins (it's what's deployed).

## Dev / deploy

- Edit `index.html` locally, commit, push to `main` → GitHub Pages rebuilds automatically.
- No install, no build, no test commands exist.

## Writing `index.html` (the only file you edit)

- SEO meta tags and Open Graph are inline in `<head>` — update together.
- CSS custom properties (`:root` vars) control colors — don't hardcode values elsewhere.
- Color tokens: `--bg`, `--surface`, `--surface-elevated`, `--surface-card`, `--text`, `--text-secondary`, `--text-muted`, `--accent`, `--accent-soft`, `--border`, `--border-subtle`, `--radius-*`.
- Typography uses SF Pro Display stack via `--font` system font stack with `-apple-system`/`BlinkMacSystemFont`. Keep this native Apple-style stack.
- Contact links (LinkedIn, GitHub) exist in both `index.html` and `README.md` — keep in sync.

## Design conventions applied (Apple-style minimal, do not break)

- **Dark appearance**: no app-specific appearance toggle. Keep the dark palette; respect `prefers-color-scheme`.
- **Focus ring**: `a:focus-visible, button:focus-visible` must keep the visible 2px `var(--accent)` outline with offset (accessibility requirement).
- **Reduced motion**: `@media (prefers-reduced-motion: reduce)` disables all transitions/animations — preserve this.
- **Backscroll**: nav uses `scroll-behavior: smooth` except under reduced motion.
- **Cards**: glass-style `backdrop-filter` panels on Hero aside, bordered `--surface-card` cards elsewhere. Border radius via `--radius-*`.
- **Transitions**: subtle `transform: translateY(-2px~-3px)` on hover for interactive elements; micro-interactions stay minimal.
- **Editorial spacing**: generous vertical padding (`clamp(80px, 12vw, 140px)`), minimal ornamentation, focus on content hierarchy.
- **Hero treatment**: expansive typography (`clamp(3.2rem, 8vw, 6.5rem)`), subtle vignette, ample negative space.
- **Project layout**: card container removed for editorial feel, projects as distinct rows with subtle dividers.
- **Tech panel**: glass morphism with restrained blur (`blur(10px)`) and elevated surface.
- **CTA treatment**: minimal gradient border, focus on typographic hierarchy over visual noise.
- **Responsive breakpoints**: 980px (nav collapse), 880px (grid to 2-col), 640px (single column stack).

## Questions

Only ask the user questions if the repo cannot answer something important. Use the `question` tool for one short batch at most.

Good questions:
- undocumented team conventions
- branch / PR / release expectations
- missing setup or test prerequisites that are known but not written down

Do not ask about anything the repo already makes clear.