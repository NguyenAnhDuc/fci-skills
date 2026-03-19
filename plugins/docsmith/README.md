# Docsmith

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)](https://github.com/NguyenAnhDuc/bss-skills)
[![Claude Code](https://img.shields.io/badge/Claude_Code-Plugin-purple.svg)](https://github.com/NguyenAnhDuc/bss-skills)

PRC-010: AI-guided documentation workflow for creating structured, high-quality docs.

Based on industry best practices from *Docs for Developers* (Bhatti et al., 2021) and *Strategic Writing for UX* (Podmajersky, 2019).

---

## ✨ Features

- 🎯 Systematic 11-step workflow from audience analysis to publication
- 🤖 AI-powered drafting with built-in quality checks
- 📊 UX content standards (voice chart, text patterns, scorecard)
- ✅ Automated verification via product walkthrough with screenshots
- 🔄 Human-in-the-loop review gates at critical stages
- 📦 Professional templates for all documentation types

---

## 🚀 Quick Start

### Installation

Claude Code (recommended):

```
/plugin marketplace add https://github.com/NguyenAnhDuc/bss-skills.git
/plugin install docsmith@bss-skills
/reload-plugins
```

### Usage

```
/fpt-smartcloud/docsmith help           # Show all commands
/fpt-smartcloud/docsmith start MyProduct # Begin full workflow
/fpt-smartcloud/docsmith draft APIEndpoint # Quick draft only
/fpt-smartcloud/docsmith verify MyProduct  # Run quality checks
```

---

## 📋 Workflow

```
audience → plan → review-plan → sitemap → voice → draft → edit → walkthrough → peer-review → [tech-review] → incorporate → publish
```

| Step | Owner | Description |
|------|-------|-------------|
| 1. audience | 👤 Human | Define target users, goals, personas |
| 2. plan | 🤖 AI | Documentation plan + traceability matrix |
| 3. review-plan | 👤 Human | Approve plan |
| 4. sitemap | 🤖 AI | Folder structure, navigation, cross-links |
| 5. voice | 🤖 AI | Voice chart, UX patterns, scorecard |
| 6. draft | 🤖 AI | Write documentation |
| 7. edit | 🤖 AI | Self-review (5 passes) |
| 8. walkthrough | 🤖 AI | Test on product + screenshots |
| 9. peer-review | 👤 Human | Review docs |
| 10. tech-review | 👤 Human | Optional technical review |
| 11. incorporate | 🤖 AI | Integrate feedback |
| 12. publish | 👤 Human | Final approval & release |

---

## 📖 Commands Reference

| Command | Alias | Owner | Description |
|---------|-------|-------|-------------|
| `help` | `h` | — | Show command reference |
| `start` | — | — | Begin full process |
| `audience` | `aud` | Human | Define audience and goals |
| `plan` | `pl` | AI | Create documentation plan |
| `review-plan` | `rp` | Human | Review and approve plan |
| `sitemap` | `sm` | AI | Create sitemap |
| `voice` | `vc` | AI | UX content standards |
| `draft` | `dr` | AI | Draft documentation |
| `edit` | `ed` | AI | Self-review edit (5 passes) |
| `walkthrough` | `wt` | AI | Product walkthrough |
| `validate` | `val` | AI | Run test cases only |
| `test` | `t` | AI | Create/update test cases |
| `verify` | `vf` | AI | Run all verification checks |
| `peer-review` | `pr` | Human | Peer review |
| `tech-review` | `tr` | Human | Technical review |
| `incorporate` | `inc` | AI | Incorporate feedback |
| `publish` | `pub` | Human | Approve and publish |

---

## 📁 Templates Included

- Audience Profile Template
- Content Type Templates
- Documentation Plan Template
- Traceability Matrix Template
- UX Content Scorecard Template
- UX Text Patterns Template
- Voice Chart Template
- Walkthrough Test Case Template
- Walkthrough Test Execution Template

---

## 📄 License

MIT
