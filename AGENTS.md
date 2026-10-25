# AGENTS.md

Guidance for AI agents and contributors working in this repository.

## Project Overview

This is a **personal portfolio website** for Md. Arifur Rahman. It is a
**static site** built with plain HTML5 and CSS3. There is no build step, no
package manager, no JavaScript framework, and no test suite.

The goal of the project is defined in `README.md` — a responsive, single-page
portfolio covering: navbar, hero (with photo and CV download), social links,
about, skills, projects (3+ cards), contact info, and footer.

## Project Structure

```
Portfolio_Arifur_Rahman/
├── index.html               # The main single-page portfolio
├── style.css                # All styles for the site (incl. detail pages)
├── project-ecommerce.html   # Project detail page 1
├── project-todo.html        # Project detail page 2
├── project-weather.html     # Project detail page 3
├── Images/                  # Profile photo, logos, project thumbnails, gallery images
├── .vscode/                 # Editor settings
├── README.md                # Portfolio task requirements/spec
└── AGENTS.md                # This file
```

- `index.html` — single-page markup. Sections in order: Header/Navbar (with
  mobile hamburger menu), Hero (`#home`), About (`#about`), Skills (`#skills`,
  categorized into Frontend / Backend / Tools), Education (`#education`),
  Experience (`#experience`), Projects (`#projects`), Gallery (`#gallery`),
  Contact (`#contact`), Footer.
- `project-*.html` — one detail page per project card, linked via
  "View More / Details" buttons. They reuse `style.css` (section 11) and carry
  tech stack, description, live/GitHub links, challenges, and future plans.
- `style.css` — all styling. Sections are numbered with comments matching the
  HTML section order (e.g. `/* 1) Header Section */`, `/* 2) Hero Section */`).
- `Images/` — all image assets. Images are referenced with relative paths
  (e.g. `./Images/LogoMyPortfolio-02.png`).

## How to Run / Preview

No build or install step is required. Open `index.html` directly in a browser,
or serve the folder with any static server:

```
# Using VS Code "Live Server" extension (recommended), or:
npx serve .
python -m http.server 8000
```

## Build, Test, and Lint Commands

There are **none**. Do not add a build system, bundler, or package manager
unless explicitly asked. There is no `package.json`. Changes can be verified by
opening `index.html` in a browser and visually checking the result.

## Coding Conventions

### HTML
- Use semantic elements: `header`, `nav`, `section`, `article`, `footer`.
- Each major section has an `id` matching its navbar anchor (e.g.
  `id="about"` ↔ `<a href="#about">`). Keep them in sync when adding or
  renaming sections.
- Keep the section comment markers in `index.html` (e.g. `<!-- About Section -->`)
  so sections stay easy to locate.
- Indentation is **4 spaces**.

### CSS
- One stylesheet: `style.css`. Do not add CSS files or inline `<style>` blocks
  (existing inline `style` attributes on `#gallery` and `#contact` are legacy —
  prefer moving new styles into `style.css`).
- Keep the numbered section comments (`/* 3) About Section */`) and add a
  matching numbered comment for any new section.
- Use **kebab-case** for class names (e.g. `project-card`, `hero-content`,
  `skill-box`).
- Common visual language to stay consistent with:
  - Accent/blue: `#3498db`
  - Dark header/footer background: `#1a252f`
  - Green (progress bars, hovers): `#2ecc71`
  - Section heading color: `#2c3e50`
  - Standard card shadow: `0 8px 16px 0 rgba(0,0,0,0.6)`
  - Border radius: 4px–15px depending on element
- Layout uses CSS Grid with `repeat(auto-fit, minmax(...))` and Flexbox for
  responsive behavior. Media queries live in **section 12** of `style.css`
  (breakpoints: 1200px, 992px, 768px, 480px) — extend those rather than
  scattering new queries.
- Indentation is **4 spaces**.

## Important Gotchas / Current State

- **Projects and Gallery sections are now enabled** (previously hidden behind
  a `displayNone` wrapper with `disabled` nav links). The `.displayNone` and
  `.disabled` CSS rules still exist as unused utilities — do not re-add the
  wrapper or `disabled` classes to the nav.
- **Project cards link to detail pages** (`project-ecommerce.html`,
  `project-todo.html`, `project-weather.html`). "Live Link" and "GitHub
  (Client)" buttons on those pages are placeholders (`href="#"`) — replace with
  real URLs when the projects are deployed.
- **"Download CV" button links to the real CV** at
  `assets/CV_Md_Arifur_Rahman.docx` via an `<a download>` tag styled with
  `.btn-primary`. To update the CV, replace the file in `assets/` (keep the
  filename, or update the `href` in `index.html`).
- There is a **commented-out scroll-hide navbar script** at the bottom of
  `index.html` (and its matching commented-out `.navbar.hide` CSS rule). Do not
  delete it without asking — it is intentionally disabled but kept for future
  use.
- **Mobile menu script**: a small vanilla-JS snippet at the bottom of
  `index.html` toggles `.active` on `<nav id="nav-menu">`. The dropdown rule is
  `header nav.active ul` inside the 768px media query — keep the JS toggle
  target and that selector in sync with `.menu-toggle` styles in `style.css`.
- **Personal details are placeholders**: the Education cards contain
  `[Your College Name]` / `[Your School Name]` / `[Passing Year]` markers, and
  the About section's last paragraph (hobbies) is marked with a comment. Update
  these with real information.
- All inline `style` attributes on `#gallery` and `#contact` have been moved
  into `style.css` — keep them there.
- `Images/` contains unused files (`ProfilePic.jpg`, `LogoMyPortfolio-03.png`).
  Do not delete them without asking.

## When Making Changes

1. Keep the site a plain static HTML/CSS project — no frameworks, no build tooling.
2. Preserve the existing section ordering, ID/anchor pairing, and comment markers.
3. Match the existing color scheme, spacing, and shadow/radius conventions.
4. Preview changes in a browser at multiple widths when touching layout.
5. Update `README.md` only if the task requirements themselves change.
6. Update this file if the project structure or conventions change.
