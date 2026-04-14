# Apply V2

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)](https://github.com/NguyenAnhDuc/bss-skills)
[![Claude Code](https://img.shields.io/badge/Claude_Code-Plugin-purple.svg)](https://github.com/NguyenAnhDuc/bss-skills)

Migrate an existing Material-UI (v1) page to the FCI Design System (v2) using the runtime `useLayout()` / `isApplyingV2` switching model.

---

## ✨ Features

- 🔀 Works with dual-runtime V1/V2 page switching
- 🧩 Uses `useLayout().components` instead of direct MUI imports
- 🧱 Standardizes pages with `PageWrapper`
- 📋 Includes migration checklist and common pitfalls
- 📚 Includes references for tables, forms, detail pages, dialogs, and tutorials
- 🎯 Built for real FPT Cloud console V2 migration work

---

## 🚀 Quick Start

### Installation

```
/plugin marketplace add https://github.com/NguyenAnhDuc/bss-skills.git
/plugin install apply-v2@bss-skills
/reload-plugins
```

### Usage

```
/fci/apply-v2 migrate vpn list page to v2
/fci/apply-v2 convert custom-image create page
/fci/apply-v2 apply v2 for security-group detail page
```

---

## 📋 What It Covers

- Register feature routes in `V2_READY_PAGES`
- Replace direct MUI imports with `useLayout().components`
- Wrap page shell with `PageWrapper`
- Migrate tables, forms, dialogs, empty states, and tutorials
- Keep V1/V2 coexistence safe at runtime

---

## 📚 Included References

- `references/tables.md`
- `references/forms.md`
- `references/detail-pages.md`
- `references/dialogs.md`
- `references/tutorials.md`

---

## 📄 License

MIT License

## 👤 Author

**BSS Team** — FPT Smart Cloud
