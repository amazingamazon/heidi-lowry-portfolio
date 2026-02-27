# Portfolio Dev Memory

## Page Status
- `ai-platform.html` — complete, fully structured per template
- `process-manager.html` — reformatted Feb 2026 to match ai-platform.html structure
- `index.html` — complete (philosophy cards, case study previews with images)
- `leadership.html` — unknown, not yet reviewed this session
- `design-coaching.html` — unknown, not yet reviewed this session

## Confirmed Case Study Page Structure (both ai-platform + process-manager)
1. Title + subtitle
2. Hero image (`.case-hero-image`) — full width, border-radius 10px, box-shadow
3. Skip link (`<a href="#visuals" class="skip-link">`) with lucide `image` icon
4. Challenge block (`.challenge`) — bg-light, 4px primary left border
5. Metadata strip (`.metadata`) — icon+label pattern using `.metadata-label` + lucide icons
6. `<h3>Strategic Approach</h3>` + `.strategy-cards` container
7. `<h3>Design Process</h3>` + `h4` subsections (plain prose + icon-lists or bullet lists)
8. `<div class="impact-section">` wrapping `<h3>Impact & Outcomes</h3>` + `.impact-grid`(s)
9. `.reflection-section` — accent gold left border, accent-light bg
10. `<section id="visuals" class="visual-examples">` — Visual Design with `.design-artifact` blocks
11. `.case-navigation` with prev/next buttons

## Page-Specific `<style>` Block (copy this to every case study)
Each case study carries its own `<style>` block defining:
- `.case-hero-image`
- `.skip-link`
- `.metadata-item` / `.metadata-label` (override global styles for icon pattern)
- `.strategy-cards` / `.strategy-card` / `.strategy-card-header`
- `.icon-list` / `.icon-list li`
- `.impact-section` (wrapper with bg-light, border, border-radius 10px)
- `.visual-section-intro`
- Mobile media query for `.strategy-cards`

## Lucide Icon Conventions
- Metadata: `user`, `calendar`, `users`, `activity`
- Strategy cards: `search`, `git-merge`, `navigation`, `handshake`, `microscope`, `map`, `trending-up`
- Icon lists: `users`, `shield`, `code-2`, `focus`, `cpu`, `layout-grid`, `database`
- Skip link: `image`
- All icons initialized with single `<script>lucide.createIcons();</script>` at end of body

## CSS Variable Notes
- Gold accent is `var(--accent)` in style.css (NOT `--accent-gold` — that name only appears in CLAUDE.md)
- Gold light bg for reflection is `var(--accent-light)`
- Success green: `var(--success)` / `var(--success-light)` — used for `.key-insight` blocks

## Key Patterns
- `.metadata-item` in the page `<style>` block overrides the global `.metadata-item` to add flex-direction: column and gap — required for icon label pattern to work
- `.strategy-card` sets `border-left: 4px solid var(--primary)` but also needs `border: 1px solid var(--border)` — both are required
- `.impact-section .impact-item { background: white; }` overrides the global white default to stay white inside the bg-light wrapper
- Case navigation uses `.case-navigation > div` from style.css for flex layout — do NOT add inline style

## See Also
- `patterns.md` — detailed component reference (to be created as needed)
