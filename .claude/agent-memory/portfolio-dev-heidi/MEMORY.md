# Portfolio Dev Memory

## REDESIGN SHIPPED — March 2026
All 5 pages now use the new editorial / Okta-presentation design language. The old style.css-based system is no longer in use. Each page is fully self-contained (all CSS inline in a `<style>` block). There is no shared stylesheet.

## Design System (current — as of March 2026)
All CSS variables live in a `:root` block inside each page's `<style>` tag.

| Variable | Value | Use |
|---|---|---|
| `--white` | `#ffffff` | backgrounds |
| `--bg` | `#F9F9F8` | tinted sections |
| `--ink` | `#111111` | headings, strong text |
| `--mid` | `#555555` | body text |
| `--light` | `#999999` | labels, meta |
| `--rule` | `#E5E4E0` | borders, dividers |
| `--blue` | `#1B4FD8` | primary accent |
| `--blue-light` | `#EEF3FF` | tag pills, highlights |
| `--blue-mid` | `#C7D7FA` | nav active states |
| `--green` | `#1A6648` | future/success states |
| `--green-light` | `#EDFAF3` | success backgrounds |
| `--amber` | `#92400E` | pull quotes |
| `--amber-light` | `#FFFBEB` | pull quote background |

## Page Status (post-redesign)
- `index.html` — complete, editorial layout, self-contained CSS
- `ai-platform.html` — complete, editorial layout + diagrams, self-contained CSS
- `process-manager.html` — complete, editorial layout + diagrams, self-contained CSS
- `leadership.html` — complete, editorial layout + diagrams, self-contained CSS
- `design-coaching.html` — complete, editorial layout, self-contained CSS

## File Structure
- No `style.css` in active use — all CSS is per-page in `<style>` blocks
- No `preview-*.html` files (deleted after shipping March 2026)
- Images still in `/images/`
- Lucide via CDN: `https://unpkg.com/lucide@latest/dist/umd/lucide.min.js`
- No build tools, no npm, no frameworks

## Nav Pattern (all pages)
```html
<nav>
  <a href="index.html" class="nav-name">Heidi Lowry</a>
  <ul class="nav-links">
    <li><a href="index.html">About</a></li>
    <li><a href="ai-platform.html">AI Platform</a></li>
    <li><a href="process-manager.html">Process Manager</a></li>
    <li><a href="leadership.html">Leadership</a></li>
    <li><a href="design-coaching.html">Coaching &amp; Craft</a></li>
    <li><a href="mailto:heidi.lowry@gmail.com">Contact</a></li>
  </ul>
</nav>
```
Active page link gets `class="active"`.

## Case Nav Order
AI Platform → Process Manager → Leadership → Coaching & Craft → back to index (Overview)

## Key Layout Patterns (new design)
- **Seam grid**: `display: grid; gap: 2px; background: var(--rule)` with white children — hairline gap illusion
- **Eyebrow**: `11px, 700 weight, 0.14em tracking, uppercase, var(--blue)`
- **Phase track**: flex row with `::before` gradient line; collapses to flex-column with row-direction cards on mobile
- **Stepper**: `.step` with `::after` connector on left; already vertical, no mobile override needed
- **Stats strip**: 4-col desktop, 2-col at ≤900px
- **Pull quote**: `border-left: 3px solid var(--amber); background: var(--amber-light)`
- **Practice grid**: 3-col desktop, 1-col at ≤900px
- **Culture grid**: 3-col desktop, 2-col at ≤900px, 1-col at ≤640px
- **Work cards** (homepage): `grid-template-columns: 3fr 2fr`; image col hidden on mobile
- **Tag pills**: `var(--blue-light)` bg, `var(--blue)` text, `border-radius: 100px`

## Responsive Breakpoints
- `≤900px` — primary mobile breakpoint
- `≤640px` — secondary (typography, padding)

## Git Workflow
- Deploy branch: `main` (GitHub Pages serves from main)
- Commit convention: `section: description`

## Lucide Icons Confirmed Valid
compass, layers, git-branch, trending-up, shield, heart, award, users, navigation, search, pen-tool, message-square, book-open, map, layout-grid, briefcase, target, handshake, focus, user-check, zap, key, check-circle, mic, link, battery-charging, calendar, globe, cpu, image, git-merge, bar-chart-2, star, x-circle, arrow-right, layout, mouse-pointer, eye, alert-circle, alert-triangle, terminal, edit-3, check-square, file-up, file-text

NOTE: `file-output` is NOT a valid Lucide icon — use `file-up` instead.

## Image Inventory (/images/)
- `ai-*.png` — AI Platform case study screenshots
- `process-solutions.png`, `process-employees.png`, `process-canvas.png`, `process-detail.png`, `process-map-view.png` — Process Manager screenshots
- `legacy-procedure-interface.png` — old standalone UI (before)
- `final-procedure-design.png` — modernized integrated UI (after)
- `option-1-prescriptive.png`, `option-2-flexible.png` — editing direction options
