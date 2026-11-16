# spfx-components

> **Reusable SharePoint Framework (SPFx) web parts for modern SharePoint Online — production-grade components built with the current toolchain (TypeScript, React, Fluent UI, PnP controls, Heft).**

[![License: Apache 2.0](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Status: Design](https://img.shields.io/badge/Status-Design-orange.svg)](#project-status)
[![SPFx](https://img.shields.io/badge/SPFx-1.21+-green.svg)](https://learn.microsoft.com/en-us/sharepoint/dev/spfx/sharepoint-framework-overview)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.0+-blue.svg)](https://www.typescriptlang.org/)

---

## Why this exists

Most organisations running SharePoint Online need the same handful of web parts over and over: a safe script loader, a configurable list-backed reporting dashboard, PnP Modern Search customisations, a FAQ renderer with structured link syntax, a modern homepage starter template. Each engagement rebuilds them, each bespoke build introduces subtle variations, and none of it accumulates into reusable IP.

`spfx-components` is a curated library of these recurring patterns — production-tested on enterprise engagements, rebuilt generically with no client-specific content, and packaged as drop-in SPFx solutions that any tenant can deploy.

## What's in the library

### Planned components

**Infrastructure**
- **`script-loader`** — Load client-side scripts and styles from the Site Assets library at page load. Enforces tenant-policy compliance (no inline scripts, no CDN references, all assets governed by SharePoint). Based on patterns proven under BBC Media Action CR-006.

**Reporting and visualisation**
- **`list-reporting-dashboard`** — Configurable dashboard that renders SharePoint List data as tables, charts, and filter panels. Use when Power BI licensing is restricted or when data stays within SPO. Supports grouping, sorting, column visibility, drill-down, export to CSV.
- **`country-rollup`** — List rollup web part aggregating items across multiple sites or list URLs with configurable field mapping.

**Search and navigation**
- **`pnp-search-templates`** — Reusable Handlebars templates library for PnP Modern Search. Includes verticals, filters, result layouts, and bookmark/acronym patterns.
- **`faq-webpart`** — FAQ renderer with structured `[Label|URL|type]` link syntax, supporting internal SharePoint links, external URLs, Teams deep links and app protocol handlers.

**Content and homepage**
- **`modern-homepage-starter`** — Reusable modern SharePoint landing page template with configurable hero area, Hot Topics cards, Quick Links, alert bar, analytics strip, and responsive mobile menu.

Each component is a standalone SPFx solution package (`.sppkg`) with full source, build scripts, and deployment guide.

## Technology stack

- **SharePoint Framework (SPFx)** 1.21 and later
- **TypeScript** 5.0+
- **React** 17/18 (per SPFx version)
- **Fluent UI** 9
- **PnP SPFx controls**
- **Heft** build toolchain (modern SPFx default)
- **Node.js** LTS
- **ESLint, Prettier** for code quality
- **Rush** or **npm workspaces** for monorepo management

Components are developed against the latest SPFx release and backward-compatibility is tested against two prior SPFx versions where feasible.

## Repository structure

```
spfx-components/
├── README.md
├── LICENSE
├── packages/
│   ├── script-loader/
│   │   ├── src/
│   │   ├── config/
│   │   ├── package.json
│   │   └── README.md
│   ├── list-reporting-dashboard/
│   ├── pnp-search-templates/
│   ├── faq-webpart/
│   ├── modern-homepage-starter/
│   └── ...
├── docs/
│   ├── deployment-guide.md
│   ├── tenant-policy-notes.md
│   └── development-setup.md
└── .github/
    └── workflows/
```

## Getting started

> **Note**: implementation has not yet started. Expected first components Q1 2027.

When available, each component will install via:

```bash
# Clone the repository
git clone https://github.com/anika-tech-solution-ltd/spfx-components.git

# Build a specific component
cd spfx-components/packages/script-loader
npm install
gulp bundle --ship
gulp package-solution --ship

# Deploy the .sppkg file to your tenant app catalog
```

Components publish as individual `.sppkg` files so you can deploy only what you need. A combined bundle with all components is published per release.

## Design principles

1. **Tenant-policy safe** — components assume realistic enterprise constraints. No external CDN dependencies. No inline scripts. All assets governed through SharePoint.
2. **Configurable, not hardcoded** — every component exposes property pane configuration rather than requiring code changes to adapt. One deployment, many uses.
3. **Accessibility first** — components meet WCAG 2.1 AA. Fluent UI primitives used where possible. Keyboard navigation and screen reader support tested.
4. **Performance-conscious** — minimal bundle size, lazy loading where sensible, no heavyweight dependencies added without justification.
5. **Zero data egress** — components never transmit SharePoint data outside the Microsoft 365 tenant. No telemetry, no external analytics, no third-party API calls without explicit configuration.
6. **Documented deployment** — each component ships with a deployment guide covering app catalog upload, permissions, configuration, and common issues.

## Project status

**Current phase**: Design. Implementation begins Q1 2027.

### Roadmap

| Phase | Period | Deliverable |
|---|---|---|
| **Phase 0** | Nov–Dec 2026 | Repository structure, this README, development setup |
| **Phase 1** | Jan–Feb 2027 | `script-loader` and `list-reporting-dashboard` v0.1 |
| **Phase 2** | Mar–Apr 2027 | `pnp-search-templates` and `faq-webpart` v0.1 |
| **Phase 3** | May–Jun 2027 | `modern-homepage-starter` and `country-rollup` v0.1 |
| **Phase 4** | Q3 2027 onward | New components added based on real-engagement patterns |

## Contributing

Contributions welcome once v0.1 ships. Component requests via GitHub issues most helpful at the current stage — tell us what recurring SPFx web part pattern you'd like to see packaged.

## Licence

This project is licensed under the **Apache License 2.0** — see [LICENSE](./LICENSE) for details. Components are freely usable in commercial engagements with attribution preserved in source files.

## Maintainer

Built by **[Anika Tech Solution Ltd](https://github.com/anika-tech-solution-ltd)** — specialist Microsoft 365, SharePoint and Anthropic Claude consultancy.

Lead: **Arvind Gupta** — Principal Consultant. 15+ years enterprise SharePoint development. Patterns derive from production engagements at BBC Media Action, Arthur Cox LLP, Deloitte Netherlands, Lincolnshire County Council, Vattenfall, Partners Capital, and Schroders plc (13 years).

**Website**: [anikatechsolution.co.uk](https://anikatechsolution.co.uk)

---

*Part of the Anika Tech Solution Ltd open-source toolkit for AI-powered enterprise content operations. See the [organisation profile](https://github.com/anika-tech-solution-ltd) for the full portfolio.*
