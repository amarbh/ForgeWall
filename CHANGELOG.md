# Changelog

All notable changes to this project are documented here. This project adheres to [Semantic Versioning](https://semver.org/).

## [1.0.0] — 2026-06-18

First public, open-source release.

### Added
- **Light & dark themes** with a toggle in the toolbar. Follows the system `prefers-color-scheme` by default; your choice is remembered locally.
- **Section search** in the sidebar (focus with `/`, press `Enter` to jump to the first match, `Esc` to clear).
- **Keyboard shortcuts:** `Ctrl`/`⌘`+`S` to export, `Ctrl`/`⌘`+`Enter` to copy the CLI, `/` to search, `Esc` to close dialogs.
- **About dialog** summarizing what the tool does, the privacy model, the keyboard shortcuts, and a pre-deployment reminder.
- **Unsaved-work guard** that warns before you navigate away from an unsaved configuration.
- **Inline SVG favicon** and proper page metadata (description, Open Graph / social tags, `theme-color`).

### Changed
- **Removed the external web-font dependency** (Google Fonts). The app now uses a pure system-font stack, so it makes **zero network requests** and works fully offline from `file://`.
- Refreshed in-app copy, the generated config header, and the footer.

### Privacy / security
- Confirmed the tool makes no outbound network requests and never persists your configuration (only the theme preference is stored locally).
- Secrets continue to render as `<PLACEHOLDER>` tokens unless you type a real value.

### Notes
- Generation logic and FortiOS 7.x CLI output are unchanged from the internal builds — only the name, packaging, and the additions above are new.
- This is an unofficial tool and is not affiliated with Fortinet, Inc.
