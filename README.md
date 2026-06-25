<p align="center">
  <img src="logo.svg" width="96" alt="Forgewall logo">
</p>

<h1 align="center">Forgewall</h1>

<p align="center">
  <strong>A free, single-file, 100% client-side builder for FortiGate (FortiOS&nbsp;7.x) CLI configuration scripts.</strong><br>
  Fill in a form, watch the CLI build itself, copy or download it. Nothing you type ever leaves your browser.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/license-MIT-blue" alt="MIT License">
  <img src="https://img.shields.io/badge/dependencies-none-success" alt="Zero dependencies">
  <img src="https://img.shields.io/badge/single%20file-HTML-orange" alt="Single file">
  <img src="https://img.shields.io/badge/works-offline-brightgreen" alt="Works offline">
</p>

---

> **Unofficial tool.** Forgewall is a community project. It is **not affiliated with, authorized, or endorsed by Fortinet, Inc.** "FortiGate" and "FortiOS" are trademarks of Fortinet, Inc., used here only to describe what the generated scripts are compatible with.

## What it is

Forgewall is a configuration *helper*, not a management platform. You describe a FortiGate setup through a clean web form — interfaces, routes, firewall objects, NAT, policies, VPNs, logging — and it emits the corresponding `config … / edit … / set … / next / end` CLI block in real time, with syntax highlighting. You then review it and paste it into your device (in a lab first — see the disclaimer).

It is a **single HTML file** with **no build step, no dependencies, no backend, and no tracking**. The entire app — markup, styles, and logic — lives in one file you can read end to end.

## Demo

- **Live (GitHub Pages):** `https://your-username.github.io/forgewall/` *(enable Pages in repo settings — see below)*
- **Offline:** download [`index.html`](index.html), double-click it, done. It runs fully offline with zero network requests.

<!-- Add a screenshot to make the README pop:
![Forgewall screenshot](docs/screenshot.png)
-->

## Features

- **Form → live CLI** with FortiOS-aware syntax highlighting and a running line count.
- **Covers 20+ configuration areas** across system, networking, objects, NAT, policy, VPN, users, and logging (full list below).
- **Placeholder tracking** — secrets and required values you haven't filled in show up as `<PLACEHOLDER>` tokens, and a badge tells you how many remain before the config is deployable.
- **Import / Export** your work as a `.json` profile to save, share, or resume later.
- **One-click sample config** to see a realistic branch-office setup.
- **Light & dark themes** (follows your system preference; your choice is remembered locally).
- **Section search** and **keyboard shortcuts** for fast navigation.
- **Fully responsive** — three-pane layout on desktop, collapsible panels on mobile.
- **Private by design** — no analytics, no network calls, and your configuration is never written to disk or storage (see [Privacy](#privacy--security)).

## Supported FortiOS configuration

| Area | Sections |
| --- | --- |
| **System** | Global (hostname, timezone, admin ports, idle timeout, GUI theme), DNS, NTP (FortiGuard or custom), Admin accounts |
| **Interfaces & Routing** | Interfaces (physical / VLAN / loopback / aggregate / software-switch; static / DHCP / PPPoE; admin access; MTU), Zones, DHCP servers, Static routes (incl. blackhole) |
| **Firewall Objects** | Addresses (subnet / IP-range / FQDN / geography), Address groups, Custom services (TCP/UDP/SCTP/ICMP/IP), Service groups, Schedules (recurring / one-time) |
| **NAT** | IP pools (source NAT), Virtual IPs (destination NAT / port forwarding) |
| **Security Policy** | Firewall policy (multiple interfaces/addresses/services, source NAT + IP pools, UTM security profiles, logging) |
| **VPN** | IPsec site-to-site (phase 1 + phase 2, optional auto-generated route, address objects, and bidirectional policies), SSL-VPN |
| **Users & Auth** | Local users, User groups |
| **Logging** | SNMP (v2c), Syslog / SIEM forwarding |

> Syntax targets **FortiOS 7.x**. Some option names, the timezone index, and default profile names are version-dependent — always verify against your specific build.

## Usage

### Run it online (GitHub Pages)
1. Push this repo to GitHub.
2. **Settings → Pages → Build and deployment**, set **Source: Deploy from a branch**, branch `main`, folder `/ (root)`.
3. Your tool goes live at `https://<your-username>.github.io/forgewall/`.

(The included empty `.nojekyll` file tells Pages to serve the file as-is.)

### Run it offline
Download `index.html` and open it in any modern browser. There's nothing to install and no connection required.

### Embed it in another page
Because it's self-contained, you can drop it into any site via an `<iframe>`:

```html
<iframe src="https://your-username.github.io/forgewall/"
        allow="clipboard-write"
        style="display:block;width:100%;height:100vh;border:0;"></iframe>
```

### Save and resume
Use **Export** to download your configuration as a `.json` profile, and **Import** to load it back later. Treat exported profiles and generated `.conf` files as sensitive — they may contain pre-shared keys and passwords if you typed them.

### Keyboard shortcuts
| Shortcut | Action |
| --- | --- |
| `/` | Focus the section search |
| `Ctrl`/`⌘` + `S` | Export profile (`.json`) |
| `Ctrl`/`⌘` + `Enter` | Copy the generated CLI |
| `Esc` | Close dialogs / clear search |

## Privacy & security

- **No backend, no analytics, no network requests.** The app loads no fonts, scripts, or assets from any CDN — open your browser's network tab and you'll see nothing leave the page.
- **No persistence of your data.** Your configuration exists only in the open tab. Forgewall never writes it to disk, cookies, or local storage; it's gone when you close the tab unless you explicitly **Export**. (The *only* thing stored locally is your light/dark theme preference.)
- **Secrets are opt-in.** Passwords and pre-shared keys render as `<PLACEHOLDER>` tokens unless you type a real value, so you can safely build and share a skeleton config.
- **You are in control.** Because it's a single readable file with no dependencies, you can audit exactly what it does — and that's encouraged.

Generated configuration is a **starting point, not a finished product**. Review every line, replace all placeholders, and validate on a non-production device before deploying.

## Contributing

Contributions are welcome — new sections, FortiOS version fixes, config presets, UX polish. Please read **[CONTRIBUTING.md](CONTRIBUTING.md)** first; it covers the project's two hard rules (stay single-file with zero dependencies, and never introduce a network call) and how to test changes.

## Disclaimer

This software is provided "as is", without warranty of any kind. The authors are not responsible for any damage, outage, misconfiguration, or security incident resulting from its use. **You** are responsible for reviewing and validating every configuration before applying it to any device. Always test in a lab first.

Forgewall is **not affiliated with or endorsed by Fortinet, Inc.** "FortiGate" and "FortiOS" are trademarks of their respective owner and are used here solely to describe compatibility.

## License

Released under the [MIT License](LICENSE). You're free to use, modify, and distribute it. If you fork or redistribute, please keep the "not affiliated with Fortinet" notice intact.
