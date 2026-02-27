# Portfolio Dev Memory

## Page Status
- `ai-platform.html` — complete with 5 HTML/CSS diagrams added Feb 2026; mobile-responsive Feb 2026
- `process-manager.html` — complete with 4 HTML/CSS diagrams added Feb 2026; mobile-responsive Feb 2026
- `index.html` — complete; mobile-responsive Feb 2026
- `leadership.html` — complete with icons + diagrams added Feb 2026; mobile-responsive Feb 2026
- `design-coaching.html` — enhanced Feb 2026: stat strip, h2-with-icon chips, section-h3-with-icon, strategy cards, coaching-flow stepper, icon-upgraded metadata, impact-section wrapper, quote-block, case-navigation; mobile-responsive

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

## Inline Visual Patterns (added Feb 2026 to process-manager.html)
- `.figure-pair` — two-column grid for before/after or option-comparison screenshots; collapses to 1-col on mobile; defined in page `<style>` block (not style.css)
- `.figure-pair .figure-label` — small blue uppercase label above image (e.g. "Before" / "Option 1"); `display: block` inside `<figure>` before `<img>`
- `.inline-figure` — full-width single screenshot, light box-shadow, italic figcaption; use inside strategy cards or prose sections
- Both use semantic `<figure>` + `<figcaption>` — not `<div>` + `<p class="caption">`
- Visual Design section at bottom still uses `div.design-artifact` + `<p class="caption">` (no change there)

## HTML/CSS Diagrams in process-manager.html (added Feb 2026)
All diagrams live in the page `<style>` block (no changes to style.css). All use `.design-artifact` as outer wrapper.

1. **Before vs. After Integration Diagram** (`.bva-diagram`) — placed after challenge block, before metadata. 3-column grid: before panel | arrow col | after panel. Before = stacked `.bva-silo` boxes. After = `.bva-platform-hub` (primary blue) + `.bva-spoke` pills. Collapses to 1-col on mobile.

2. **Persona Bridge** (`.persona-bridge`) — inside Strategy Card 2. 5-column grid: lob node | arrow | connector node (Ana, primary blue) | arrow | tech node. `.persona-connect-arrow` dividers carry directional gradient lines + small label. Collapses to 1-col on mobile.

3. **Phase Track** (`.phase-track`) — inside Strategy Card 3, replaces old `.strategy-timeline`. Flex row with `::before` pseudo-element track line. Each `.phase-card` = circle number + body card. States: default (past/done), `.active` (primary blue, current), `.future` (success green). Collapses to flex-column with row-direction cards on mobile.

4. **Impact Metrics Row** (`.impact-metrics-row`) — top of impact section, before existing `.impact-grid`. 4-column grid of `.impact-metric-card` with large `.imc-stat` number, `.imc-label`, `.imc-desc`. Separated from detail grids below by `.impact-divider` (hr). Collapses to 2-col on mobile.

New Lucide icons confirmed valid: `x-circle`, `check-circle`, `book-open`, `zap`, `layout`, `arrow-right`, `briefcase`, `user-check`, `terminal`, `message-square`, `edit-3`, `check-square`, `file-up`, `file-text`, `cpu`
NOTE: `file-output` is NOT a valid Lucide icon — use `file-up` instead for document generation metaphor.

## HTML/CSS Diagrams in ai-platform.html (added Feb 2026)
All diagrams live in the page `<style>` block. All use `.design-artifact` as outer wrapper except Diagrams 2 and 5 which are embedded inside `.strategy-card` bodies without the outer wrapper.

1. **Before vs. After Fragmentation Diagram** (`.bva-diagram`) — after challenge block, before metadata. Same pattern as process-manager BvA: 3-col grid, before silos | arrow | after hub. Before = 5 isolated capability silos. After = primary blue AI hub + bva-spoke pills for all 6 capabilities. Collapses to 1-col on mobile.

2. **Persona Entry Points** (`.persona-entry`) — inside Strategy Card 2, after key-insight quote + bullets. 3-node layout: Business User (left) → AI Generation Layer (center, primary blue) → Technical User (right). Uses `.pe-node`, `.pe-icon`, `.pe-name`, `.pe-detail`, `.pe-connect`, `.pe-line`, `.pe-label`. Collapses to 1-col on mobile. Followed by `.pe-insight` (success green, same as `.persona-insight`).

3. **Adaptive Interaction Mode Phase Track** (`.phase-track`) — standalone `design-artifact` after "Key Design Decisions" bullets. 3 phases (Exploration/Chat AI, Refinement/Inline AI, Finalization/Manual Edit). Icons in phase circles: `message-square`, `edit-3`, `check-square`. Phases: default, active (primary), future (success green). Same `.phase-card`, `.phase-number`, `.phase-body`, `.phase-heading`, `.phase-audience`, `.phase-goal-tag` pattern as process-manager.

4. **Impact Metrics Row** (`.impact-metrics-row`) — top of `.impact-section`, before existing `.impact-grid`. 4 cards: 1 Designer Promoted / 3 Interaction Modes / Checkmark (patterns adopted) / 6→1 Capabilities Unified. Same `.imc-stat`, `.imc-label`, `.imc-desc` pattern + `.impact-divider` hr. Collapses to 2-col on mobile.

5. **Platform Capabilities Architecture** (`.cap-architecture`) — inside Strategy Card 1, after bullets. Hub-and-spoke: `.cap-ai-hub` (primary blue, full width) at top + `.cap-connector-row` (6 vertical lines) + `.cap-grid` (3×2 grid of `.cap-item` pills with icons). Uses `cpu` icon in hub. Collapses to 2-col grid on mobile.

## Image Inventory (/images/)
- `ai-*.png` — AI Platform case study only (5 files)
- `process-solutions.png` — Solutions home / platform nav hero
- `process-employees.png` — Folder structure / status indicators
- `process-canvas.png` — Full process map canvas
- `process-detail.png` — Detail view + embedded map
- `process-map-view.png` — Simplified linear workflow
- `legacy-procedure-interface.png` — Old standalone UI (the "before")
- `final-procedure-design.png` — Modernized integrated UI (the "after")
- `option-1-prescriptive.png` — Prescriptive editing direction
- `option-2-flexible.png` — Flexible/open editing direction

## Mobile Responsiveness (completed Feb 2026)
All 5 pages are fully responsive. Key decisions:

**Navigation**: Hamburger toggle on all pages at ≤768px. `.nav-toggle` (hidden by default, flex at ≤768px). `.nav-links` collapses to `display: none` and opens with `.open` class. Dropdown is `position: absolute; top: 70px` relative to the sticky `.nav`. Toggle script at bottom of each page swaps icon between `menu` and `x`. All pages required adding `<script src="lucide">` to `leadership.html` and `design-coaching.html` (they had none before).

**style.css breakpoints**:
- `≤768px` — hamburger, 1-col grids (philosophy, work, impact), 2-col metadata, diagram reflows, reduced artifact padding
- `≤640px` — h1→2rem, h2→1.5rem, h3→1.25rem, container padding 1.25rem/1rem, section padding reduced, case-preview-content padding 1.25rem
- `≤480px` — h1→1.75rem, h2→1.35rem, h3→1.125rem, metadata→1-col, design-artifact→1rem padding

**Per-page additions**:
- `index.html`: `.case-preview-content` padding drops to 1.25rem at ≤640px (in page style block)
- `leadership.html`: `.leadership-intro`, `.looking-forward`, `.quote-block` padding reduced at ≤640px (in page style block)
- `design-coaching.html`: `.evaluation-card` padding reduced at ≤640px (in page style block)
- `ai-platform.html` + `process-manager.html`: `.strategy-card` and `.impact-section` padding reduced at ≤768px and ≤480px (in page style blocks); `.cap-grid` → 1-col at ≤480px

**Inline figure notes**: `.figure-pair` / `.inline-figure` classes referenced in MEMORY but NOT present in process-manager.html — they were forward-looking notes and were never built.

## HTML/CSS Diagrams and Patterns in leadership.html (added Feb 2026)
All defined in the page `<style>` block. No changes to style.css.

1. **Experience stats strip** (`.experience-stats`) — 4-col grid of `.exp-stat-card` with icon, large number/label. Collapses to 2-col at ≤768px. Placed between hero and leadership-intro block.

2. **Section h2 with icon** (`.h2-with-icon`) — flex row, icon + `<h2>` element, used on every major section heading. Icon is `var(--primary)`.

3. **Section h3 with icon** (`.section-h3-with-icon`) — flex row, icon (20px) + `<span>` text. Used in place of bare `<h3>` inside sections. Avoids the global h3 `::before` left bar (which is not suppressed here — note `.section-h3-with-icon` is a div/flex wrapper, not an `<h3>` tag).

4. **Icon list** (`.icon-list`) — same pattern as case studies. Defined per-page (not in style.css on leadership page). Flex-column, gap 0.75rem, icon + span per item.

5. **30-60-90 phase track** — uses `.phase-track`, `.phase-card`, `.phase-number`, `.phase-body`, `.phase-heading`, `.phase-goal-tag`. Same pattern as ai-platform + process-manager phase tracks. Collapses to flex-column row-direction cards on mobile. Wrapped in `.design-artifact`.

6. **Ambiguity process flow** (`.ambiguity-flow`) — vertical numbered stepper. Each `.ambiguity-step` has `.ambiguity-step-num` (32px blue circle) + `.ambiguity-step-body` (strong title + p). Connector line drawn with `::after` pseudo-element on each non-last step (left: 15px, top: 32px, width: 2px). No mobile changes needed — already vertical.

7. **Practice cards** (`.practice-cards`) — 3-col grid of `.practice-card` with icon, h4, p. Used for Distributed Teams section. Collapses to 1-col at ≤768px.

8. **Culture grid** (`.culture-grid`) — 3-col grid of `.culture-card` (bg-light, icon + p). Used for "What Designers Say" section. Collapses to 2-col at ≤768px, 1-col at ≤480px.

New Lucide icons confirmed valid on leadership.html: `compass`, `award`, `pen-tool`, `map`, `bar-chart-2`, `target`, `star`, `key`, `mic`, `link`, `battery-charging`, `globe`

## HTML/CSS Diagrams and Patterns in design-coaching.html (added Feb 2026)
All defined in the page `<style>` block. No changes to style.css.

1. **Stat cards strip** (`.coaching-stats`) — 4-col grid of `.coaching-stat-card`, same visual pattern as `.experience-stats` on leadership.html but with coaching-specific class names to avoid conflicts. Collapses to 2-col at ≤768px. Placed after hero, before case study section.

2. **Coaching process stepper** (`.coaching-flow`) — vertical numbered stepper. Same structure as `.ambiguity-flow` on leadership.html: `.coaching-step` + `.coaching-step-num` (32px blue circle) + `.coaching-step-body`. Connector drawn with `::after` pseudo-element. Wrapped in `.design-artifact`. No mobile override needed — already vertical.

3. **Three evaluation lenses as strategy cards** (`.strategy-cards` / `.strategy-card`) — same pattern as case studies. Replaces the old `.impact-grid` that held these three lenses. Cards use `layout`, `mouse-pointer`, `users` icons.

4. **Metadata with icons** — `.metadata-label` pattern (icon + uppercase text + span value), same as ai-platform and process-manager. Overrides global `.metadata-item` in the page style block.

5. **`h2-with-icon` / `.section-icon-chip`** — exact same classes and CSS as leadership.html. Used on "My Coaching Approach", "The Design Options", "Strategic Decision & Evolution", "Impact & Outcomes".

6. **`section-h3-with-icon`** — same class as leadership.html. Used for "Current State" and "Three Evaluation Lenses" subsections. Note: apply `style="margin-top: 3rem;"` on the first one after `.status-badge` to preserve spacing.

7. **`category-header` upgrade** — added `display: flex; align-items: center; gap: 0.5rem;` and an icon (`eye` for visual analysis, `mouse-pointer` for interaction analysis) to each `.category-header` inside the evaluation framework.

8. **`quote-block`** — same CSS as leadership.html. Placed after the "Strategic Decision" prose, before the Impact section. Uses `var(--accent)` / `var(--accent-light)`.

9. **`impact-section` wrapper** — same as ai-platform/process-manager: bg-light, border, border-radius 10px, `.impact-item { background: white }` override.

10. **Case navigation** — `.case-navigation` + `.case-navigation > div` (flex, space-between from style.css). Links to Process Manager (prev) and Leadership (next).

New Lucide icons confirmed valid on design-coaching.html: `layers`, `mouse-pointer`, `git-branch`, `alert-circle`, `alert-triangle`, `eye`, `layout`

## See Also
- `patterns.md` — detailed component reference (to be created as needed)
