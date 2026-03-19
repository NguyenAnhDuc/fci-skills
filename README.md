# BSS Skills

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Claude Code](https://img.shields.io/badge/Claude_Code-Marketplace-purple.svg)](https://github.com/NguyenAnhDuc/bss-skills)
[![Skills](https://img.shields.io/badge/skills-2-green.svg)](https://github.com/NguyenAnhDuc/bss-skills)

AI Skills mono-repo for FPT Cloud BSS team. Claude Code plugins for documentation, cloud architecture, and more.

---

## 📦 Skills

| Skill | Command | Description |
|-------|---------|-------------|
| [Docsmith](plugins/docsmith/) | `/fpt-smartcloud/docsmith` | AI-guided documentation workflow (PRC-010) |
| [Cloud Architect](plugins/cloud-architect/) | `/fpt-smartcloud/cloud-architect` | Cloud architecture design across AWS/Azure/GCP |

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
/fpt-smartcloud/docsmith start PaymentAPI    # Full workflow
/fpt-smartcloud/docsmith draft UserManagement # Quick draft
/fpt-smartcloud/docsmith verify MyProduct     # Quality checks
```

**Workflow:**
```
audience → plan → review-plan → sitemap → voice → draft → edit → walkthrough → peer-review → incorporate → publish
```

| Command | Alias | Owner | Description |
|---------|-------|-------|-------------|
| help | h | — | Show command reference |
| start | — | — | Begin full process |
| audience | aud | 👤 Human | Define audience & goals |
| plan | pl | 🤖 AI | Create doc plan |
| review-plan | rp | 👤 Human | Review gate |
| sitemap | sm | 🤖 AI | Create structure |
| voice | vc | 🤖 AI | UX content standards |
| draft | dr | 🤖 AI | Write docs |
| edit | ed | 🤖 AI | Self-review (5 passes) |
| walkthrough | wt | 🤖 AI | Test on product |
| validate | val | 🤖 AI | Re-run tests only |
| test | t | 🤖 AI | Create test cases |
| verify | vf | 🤖 AI | Run all checks |
| peer-review | pr | 👤 Human | Peer review |
| tech-review | tr | 👤 Human | Technical review |
| incorporate | inc | 🤖 AI | Integrate feedback |
| publish | pub | 👤 Human | Final approval |

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

```
/fpt-smartcloud/cloud-architect             # Start architecture design
```

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

## 🏗️ Team Deployment

For BSS/Engineering teams:

1. **Claude Code (recommended):**
   ```
   claude plugin marketplace add https://github.com/NguyenAnhDuc/bss-skills.git
   claude plugin install docsmith@bss-skills
   ```

2. **Cursor / Other agents:**
   ```bash
   cd /path/to/your-project
   mkdir -p .cursor/agents
   git clone https://github.com/NguyenAnhDuc/bss-skills.git .cursor/agents/bss-skills
   git add .cursor/
   git commit -m "Add BSS Skills"
   ```

3. **Adding new skills:**
   ```
   plugins/<skill-name>/
   ├── skills/<skill-name>/
   │   ├── SKILL.md
   │   └── references/
   └── README.md
   ```
   Update `.claude-plugin/marketplace.json` and push.

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

Based on FPT Smart Cloud internal standards.

---

## 🐛 Support

- Issues: [GitHub Issues](https://github.com/NguyenAnhDuc/bss-skills/issues)
- Discussions: [GitHub Discussions](https://github.com/NguyenAnhDuc/bss-skills/discussions)

---

## ⭐ Star History

If you find BSS Skills useful, please consider starring the repo!

[![Star History Chart](https://api.star-history.com/svg?repos=NguyenAnhDuc/bss-skills&type=Date)](https://star-history.com/#NguyenAnhDuc/bss-skills&Date)

---

Built with ❤️ for better documentation & cloud architecture
