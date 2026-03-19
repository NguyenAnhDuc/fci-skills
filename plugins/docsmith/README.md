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

```
/plugin marketplace add https://github.com/NguyenAnhDuc/bss-skills.git
/plugin install docsmith@bss-skills
/reload-plugins
```

### Usage

```
/fci/docsmith help              # Show all commands
/fci/docsmith start MyProduct   # Begin full workflow
/fci/docsmith draft APIEndpoint # Quick draft only
/fci/docsmith verify MyProduct  # Run quality checks
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

| Command | Alias | Description | Example |
|---------|-------|-------------|---------|
| help | h | Show command reference | /fci/docsmith help |
| start | — | Begin full process | /fci/docsmith start MyProduct |
| audience | aud | Define audience & goals | /fci/docsmith aud PaymentAPI |
| plan | pl | AI creates doc plan | /fci/docsmith plan PaymentAPI |
| review-plan | rp | Human review gate | /fci/docsmith rp PaymentAPI |
| sitemap | sm | AI creates structure | /fci/docsmith sm PaymentAPI |
| voice | vc | UX content standards | /fci/docsmith vc PaymentAPI |
| draft | dr | AI writes docs | /fci/docsmith draft PaymentAPI |
| edit | ed | AI self-review (5 passes) | /fci/docsmith ed PaymentAPI |
| walkthrough | wt | Test on real product | /fci/docsmith wt PaymentAPI |
| validate | val | Re-run tests only | /fci/docsmith val PaymentAPI |
| test | t | Create test cases | /fci/docsmith test PaymentAPI |
| verify | vf | Run all checks | /fci/docsmith verify PaymentAPI |
| peer-review | pr | Human peer review | /fci/docsmith pr PaymentAPI |
| tech-review | tr | Technical review | /fci/docsmith tr PaymentAPI |
| incorporate | inc | Integrate feedback | /fci/docsmith inc PaymentAPI |
| publish | pub | Final approval | /fci/docsmith pub PaymentAPI |

---

## 💡 Examples

### Document new API

```
/fci/docsmith start PaymentAPI
# Follow prompts: audience → plan → draft → walkthrough → publish
```

### Update existing docs

```
/fci/docsmith draft UserManagement
/fci/docsmith verify UserManagement
```

### Quality check specific files

```
/fci/docsmith verify MyProduct docs/drafts/getting-started.md
/fci/docsmith verify MyProduct docs/drafts/api-*.md
```

---

## 📂 Output Structure

```
docs/
├── plan/
│   ├── audience-profile.md
│   ├── documentation-plan.md
│   └── traceability-matrix.md
├── standards/
│   ├── voice-chart.md
│   ├── ux-text-patterns.md
│   └── ux-content-scorecard.md
├── drafts/
│   ├── getting-started.md
│   ├── tutorials/
│   ├── reference/
│   └── api/
├── walkthrough/
│   ├── test-cases.md
│   └── test-execution.md
└── images/
    └── walkthrough/
```

---

## 🎨 Templates Included

- ✅ Audience Profile
- ✅ Documentation Plan
- ✅ Traceability Matrix
- ✅ Voice Chart
- ✅ UX Text Patterns
- ✅ UX Content Scorecard
- ✅ Walkthrough Test Cases
- ✅ Content Type Templates:
  - Getting Started
  - Tutorials
  - How-To Guides
  - Reference
  - API Documentation
  - Troubleshooting

---

## 📚 References

- [SKILL.md](skills/docsmith/SKILL.md) — Full process reference
- [tools-reference.md](skills/docsmith/tools-reference.md) — Tools & utilities

---

## 📄 License

MIT License

## 👤 Author

**BSS Team** — FPT Smart Cloud
