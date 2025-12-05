# Repository Guidelines

## Project Structure & Module Organization
- `index.html`: Single-page replica of the original leave-request view; treat it as the source of truth for markup and inline scripts.
- `Content/`: Stylesheets and supporting UI libraries, organized under `css/` and `mui/` subdirectories to mirror the legacy paths.
- `bundles/`: Third-party JavaScript bundles captured from the upstream site (`jquery.js`, `modernizr.js`, `bootstrap.js`).
- `Scripts/layer/`: Layered modal library required for alert and confirm dialogs.
- `Images/`: Static assets (currently `pass.png`) referenced by the page.
- Frozen copies of the crawled assets (`*.txt`) are retained at the repository root for provenance; do not modify them unless regenerating the mirror.

## Build, Test, and Development Commands
- `npx http-server .` (Node ≥18) — spins up a local static server at `http://localhost:8080` for cross-browser testing.
- `python -m http.server 8000` — lightweight alternative if Python is available; serves the site from the repository root.
- `npm install --global live-server` followed by `live-server` — auto-reloads when editing HTML/CSS/JS.

## Coding Style & Naming Conventions
- HTML: Maintain existing indentation (4 spaces) and keep inline comments concise; prefer semantic tags when expanding content.
- CSS: Stick to lowercase, hyphenated class names. Place shared rules in `Content/css/site.css`; component-specific tweaks belong in `Content/mui/css/app.css`.
- JavaScript: Use ES5-compatible syntax to match bundled libraries. Attach new scripts with relative paths and avoid inline `<script>` blocks unless mirroring legacy behavior.

## Testing Guidelines
- No automated test suite exists; perform manual verification in Chrome and one evergreen browser (Edge/Firefox) after each change.
- Validate responsive behavior by toggling DevTools device emulation and ensuring key actions (cancel, remind) show the expected layer dialogs.
- Use `Ctrl+Shift+J` (Chrome) to monitor the console; treat any new warnings or errors as blockers.

## Commit & Pull Request Guidelines
- Commit messages: Imperative tone (`Fix header alignment`, `Add print stylesheet`), scoped to a single logical change. Reference related assets or sections when possible.
- Pull requests: Provide a concise summary, list manual test steps and results, and attach screenshots or GIFs when UI changes are visible.
- Link to issue IDs when applicable using `Refs #123` or `Fixes #123` syntax so downstream automation can parse relationships.***
