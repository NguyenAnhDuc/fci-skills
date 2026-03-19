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
/fpt-smartcloud/docsmith help              # Show all commands
/fpt-smartcloud/docsmith start MyProduct   # Begin full workflow
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

| Command | Alias | Description | Example |
|---------|-------|-------------|---------|
| help | h | Show command reference | /docsmith help |
| start | — | Begin full process | /docsmith start MyProduct |
| audience | aud | Define audience & goals | /docsmith aud PaymentAPI |
| plan | pl | AI creates doc plan | /docsmith plan PaymentAPI |
| review-plan | rp | Human review gate | /docsmith rp PaymentAPI |
| sitemap | sm | AI creates structure | /docsmith sm PaymentAPI |
| voice | vc | UX content standards | /docsmith vc PaymentAPI |
| draft | dr | AI writes docs | /docsmith draft PaymentAPI |
| edit | ed | AI self-review (5 passes) | /docsmith ed PaymentAPI |
| walkthrough | wt | Test on real product | /docsmith wt PaymentAPI |
| validate | val | Re-run tests only | /docsmith val PaymentAPI |
| test | t | Create test cases | /docsmith test PaymentAPI |
| verify | vf | Run all checks | /docsmith verify PaymentAPI |
| peer-review | pr | Human peer review | /docsmith pr PaymentAPI |
| tech-review | tr | Technical review | /docsmith tr PaymentAPI |
| incorporate | inc | Integrate feedback | /docsmith inc PaymentAPI |
| publish | pub | Final approval | /docsmith pub PaymentAPI |

---

## 💡 Examples

### Document new API

```
/docsmith start PaymentAPI
# Follow prompts: audience → plan → draft → walkthrough → publish
```

### Update existing docs

```
/docsmith draft UserManagement
/docsmith verify UserManagement
```

### Quality check specific files

```
/docsmith verify MyProduct docs/drafts/getting-started.md
/docsmith verify MyProduct docs/drafts/api-*.md
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

## 🛠️ Cross-Platform Support

| Platform | Installation | Trigger | Auto-invoke |
|----------|--------------|---------|-------------|
| Claude Code | Plugin marketplace | /docsmith | ❌ Disabled |

---

## 🏗️ Team Deployment

For BSS/Engineering teams:

1. Add to project repo:
   ```
   cd /path/to/your-project
   mkdir -p .cursor/agents
   git clone https://github.com/NguyenAnhDuc/bss-skills.git .cursor/agents/bss-skills
   git add .cursor/
   git commit -m "Add BSS Skills (DocSmith + more)"
   ```

2. Team members pull:
   ```
   git pull
   # Cursor auto-detects agent
   ```

3. Usage:
   ```
   "Use docsmith to document the new OAuth2 flow"
   ```

---

## 📚 Documentation

- Process Reference: [SKILL.md](skills/docsmith/SKILL.md)
- Tools Reference: [skills/docsmith/tools-reference.md](skills/docsmith/tools-reference.md)

---

## 🤝 Contributing

Contributions welcome! Please:
1. Fork the repo
2. Create feature branch (`git checkout -b feature/amazing-feature`)
3. Commit changes (`git commit -m 'Add amazing feature'`)
4. Push to branch (`git push origin feature/amazing-feature`)
5. Open Pull Request

---

## 📄 License

MIT License

---

## 👤 Author

**Duc Nguyen**
- GitHub: [@NguyenAnhDuc](https://github.com/NguyenAnhDuc)
- Email: nguyenanhduc01120@gmail.com

Based on FPT Smart Cloud PRC-010 documentation standard.
