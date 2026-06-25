# Contributing to Forgewall

Thanks for your interest in improving Forgewall! New configuration sections, FortiOS version fixes, presets, accessibility, and UX polish are all welcome.

Before you open a pull request, please read the two hard rules below. They are what make Forgewall trustworthy, and PRs that break them can't be merged.

## The two hard rules

1. **It stays a single, dependency-free HTML file.**
   Everything — markup, CSS, and JavaScript — lives in `index.html`. No build step, no bundler, no npm packages, no external scripts, stylesheets, fonts, or images loaded from a CDN. If you need an icon, draw it as inline SVG. If you need a font, use the system font stack that's already defined.

2. **It never makes a network request.**
   Forgewall's core promise is that *nothing you type leaves your browser*. The app must make **zero** outbound requests — no `fetch`, no `XMLHttpRequest`, no telemetry, no analytics, no remote assets, no "phone home" of any kind. This is non-negotiable. A reviewer should be able to open the browser's network tab, use every feature, and see nothing leave the page.

Related expectations:
- **Don't persist the user's configuration.** Their config lives only in the open tab. Don't write it to `localStorage`, `sessionStorage`, cookies, IndexedDB, or anywhere else. (The single exception already in the code is the non-sensitive light/dark **theme** preference.)
- **Keep secrets as placeholders by default.** Passwords and pre-shared keys should emit `<PLACEHOLDER>` tokens unless the user explicitly types a value.

## Adding or changing a configuration section

The app is data-driven. Each FortiOS feature is an entry in the `MODULES` object with:
- a `fields` array describing the form inputs, and
- a `gen()` function that returns the CLI string for that section.

To add a section:
1. Add a new entry to `MODULES` with its `fields` and `gen()`.
2. Reference its id in the `NAV` array (so it appears in the sidebar) and in `OUTPUT_ORDER` (so it's placed correctly in the assembled script).
3. If useful, add a matching entry to the `EXAMPLE` object so the sample config demonstrates it.

**Accuracy matters most.** This tool generates configuration that people may apply to production firewalls. Please:
- Verify your CLI against real FortiOS 7.x syntax (lab device or official docs).
- Note any version-specific behavior in the field `help` text or section `desc`.
- Prefer safe defaults and emit placeholders for anything sensitive or required.

## Testing your change

There's no test framework to install — just verify by hand:

1. **Open `index.html` directly** in a browser (double-click / `file://`). It must work fully offline.
2. **Exercise your section:** fill the fields, load the **Example**, and confirm the generated CLI is correct and the line/placeholder counts update.
3. **Check the network tab** (DevTools) and confirm **no requests** are made.
4. **Quick syntax check** (optional, if you have Node):
   ```bash
   # extract and lint the inline script
   node -e "const fs=require('fs');const h=fs.readFileSync('index.html','utf8');require('fs').writeFileSync('/tmp/app.js',h.match(/<script>([\s\S]*)<\/script>/)[1]);" && node --check /tmp/app.js
   ```
5. Test both **light and dark** themes and a **narrow (mobile) viewport**.

## Reviewing pull requests

If you help review, the most important checks are the trust ones: **no new dependencies, no network calls, no data persistence.** Read the diff specifically for any `fetch`/`XMLHttpRequest`/remote URL/storage API before evaluating anything else.

## Style

Match the existing style in `index.html`: compact, vanilla JS (no frameworks), CSS variables for theming, and inline SVG for icons. Keep it readable — the fact that anyone can audit the whole file in one sitting is a feature.

Thanks again! 🛠️
