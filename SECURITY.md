# Security Policy

## The privacy model

Forgewall is designed so that there is very little to attack:

- **It runs entirely in your browser.** There is no backend, no account system, and no server that ever sees your data.
- **It makes no network requests.** No fonts, scripts, or assets are fetched from any CDN, and no telemetry or analytics is collected. You can verify this in your browser's network tab, and you can run the file completely offline.
- **It does not persist your configuration.** Your config lives only in the open tab and is gone when you close it, unless you explicitly use **Export**. The only thing written to local storage is your non-sensitive light/dark theme preference.

## Handling sensitive data

- Passwords and pre-shared keys are emitted as `<PLACEHOLDER>` tokens unless you type a real value, so you can build and share a skeleton config safely.
- If you *do* type real secrets, then **exported `.json` profiles and downloaded `.conf` files contain those secrets in plaintext.** Treat those files as sensitive: store them securely, don't commit them to public repositories, and delete them when you're done.
- Generated configuration is a starting point. Review every line and validate on a non-production device before deploying.

## Reporting a vulnerability

If you find a security issue — for example, anything that would cause the tool to transmit data off the page, persist secrets unexpectedly, or execute untrusted input — please report it:

1. Open a **private security advisory** via the repository's **Security → Report a vulnerability** tab (GitHub), or
2. Open a regular issue **only if** the problem is not sensitive.

Please include steps to reproduce and the browser/version you used. Because this is a community project, fixes are made on a best-effort basis, but trust-related issues (network calls, data leakage, persistence of secrets) are treated as the highest priority.

## Supported versions

This project ships as a single file; the latest version in the `main` branch is the supported one. If you're running an older copy, grab the current `index.html`.
