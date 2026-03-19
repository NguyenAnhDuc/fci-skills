# BSS Skills

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Claude Code](https://img.shields.io/badge/Claude_Code-Marketplace-purple.svg)](https://github.com/NguyenAnhDuc/bss-skills)
[![Skills](https://img.shields.io/badge/skills-2-green.svg)](https://github.com/NguyenAnhDuc/bss-skills)

AI Skills mono-repo for FPT Cloud BSS team. Claude Code plugins for documentation, cloud architecture, and more.

---

## 📦 Skills

| Skill | Command | Description |
|-------|---------|-------------|
| [Docsmith](plugins/docsmith/) | `/fci/docsmith` | AI-guided documentation workflow (PRC-010) |
| [Cloud Architect](plugins/cloud-architect/) | `/fci/cloud-architect` | Cloud architecture design across AWS/Azure/GCP |

---

## 🚀 Quick Start

### Installation

```bash
# Add marketplace (one time)
claude plugin marketplace add https://github.com/NguyenAnhDuc/bss-skills.git

# Install skills
claude plugin install docsmith@bss-skills
claude plugin install cloud-architect@bss-skills

# Reload
/reload-plugins
```

### Update

```bash
claude plugin marketplace update bss-skills
claude plugin update docsmith@bss-skills
claude plugin update cloud-architect@bss-skills
```

---

## 🤖 Docsmith

PRC-010: Systematic documentation workflow from audience analysis to publication.

```
/fci/docsmith start PaymentAPI    # Full workflow
/fci/docsmith draft UserManagement # Quick draft
/fci/docsmith verify MyProduct     # Quality checks
```

**Workflow:**
```
audience → plan → review-plan → sitemap → voice → draft → edit → walkthrough → peer-review → incorporate → publish
```

| Command | Alias | Owner | Description | Example |
|---------|-------|-------|-------------|---------|
| help | h | — | Show command reference | /fci/docsmith help |
| start | — | — | Begin full process | /fci/docsmith start MyProduct |
| audience | aud | 👤 Human | Define audience & goals | /fci/docsmith aud PaymentAPI |
| plan | pl | 🤖 AI | Create doc plan | /fci/docsmith plan PaymentAPI |
| review-plan | rp | 👤 Human | Review gate | /fci/docsmith rp PaymentAPI |
| sitemap | sm | 🤖 AI | Create structure | /fci/docsmith sm PaymentAPI |
| voice | vc | 🤖 AI | UX content standards | /fci/docsmith vc PaymentAPI |
| draft | dr | 🤖 AI | Write docs | /fci/docsmith draft PaymentAPI |
| edit | ed | 🤖 AI | Self-review (5 passes) | /fci/docsmith ed PaymentAPI |
| walkthrough | wt | 🤖 AI | Test on product | /fci/docsmith wt PaymentAPI |
| validate | val | 🤖 AI | Re-run tests only | /fci/docsmith val PaymentAPI |
| test | t | 🤖 AI | Create test cases | /fci/docsmith test PaymentAPI |
| verify | vf | 🤖 AI | Run all checks | /fci/docsmith verify PaymentAPI |
| peer-review | pr | 👤 Human | Peer review | /fci/docsmith pr PaymentAPI |
| tech-review | tr | 👤 Human | Technical review | /fci/docsmith tr PaymentAPI |
| incorporate | inc | 🤖 AI | Integrate feedback | /fci/docsmith inc PaymentAPI |
| publish | pub | 👤 Human | Final approval | /fci/docsmith pub PaymentAPI |

**Output Structure:**
```
docs/
├── plan/           # audience-profile, doc-plan, traceability-matrix
├── standards/      # voice-chart, ux-patterns, scorecard
├── drafts/         # getting-started, tutorials, reference, api
├── walkthrough/    # test-cases, test-execution
└── images/         # walkthrough screenshots
```

**Templates:** Audience Profile, Documentation Plan, Traceability Matrix, Voice Chart, UX Text Patterns, UX Content Scorecard, Walkthrough Test Cases, Content Type Templates (Getting Started, Tutorials, How-To, Reference, API, Troubleshooting)

📖 [Full Docsmith README](plugins/docsmith/README.md)

---

## ☁️ Cloud Architect

Design cloud architectures, migration plans, cost optimization across AWS/Azure/GCP.

**Core Workflow:**
```
Discovery → Design → Security → Cost Model → Migration → Operate
```

**Reference Guides:** AWS Services, Azure Services, GCP Services, Multi-Cloud, Cost Optimization

**Key Capabilities:**
- 🏗️ Architecture design with HA (99.9%+)
- 🔒 Zero-trust security (IAM, encryption)
- 💰 Cost optimization (reserved, spot, right-sizing, FinOps)
- 🔄 Migration planning (6Rs framework)
- 📊 Monitoring & continuous optimization
- 🛡️ Disaster recovery (RTO/RPO)

📖 [Full Cloud Architect SKILL.md](plugins/cloud-architect/skills/cloud-architect/SKILL.md)

---

## 📄 License

MIT License

## 👤 Author

**Duc Nguyen** — [@NguyenAnhDuc](https://github.com/NguyenAnhDuc)

Based on FPT Smart Cloud internal standards.

---

## ⭐ Star History

[![Star History Chart](https://api.star-history.com/svg?repos=NguyenAnhDuc/bss-skills&type=Date)](https://star-history.com/#NguyenAnhDuc/bss-skills&Date)

---

Built with ❤️ for better documentation & cloud architecture
