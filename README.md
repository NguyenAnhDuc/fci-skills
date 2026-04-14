# BSS Skills

Skills repo for the FPT Cloud BSS team.

## Available skills

| Skill | Command | Purpose |
| --- | --- | --- |
| [Docsmith](plugins/docsmith/) | `/fci/docsmith` | Documentation workflow |
| [Cloud Architect](plugins/cloud-architect/) | `/fci/cloud-architect` | Cloud architecture and migration planning |
| [Apply V2](plugins/apply-v2/) | `/fci/apply-v2` | Migrate Material-UI v1 pages to FCI Design System v2 |

## Install

```bash
claude plugin marketplace add https://github.com/NguyenAnhDuc/bss-skills.git
claude plugin install docsmith@bss-skills
claude plugin install cloud-architect@bss-skills
claude plugin install apply-v2@bss-skills
/reload-plugins
```

## Update

```bash
claude plugin marketplace update bss-skills
claude plugin update docsmith@bss-skills
claude plugin update cloud-architect@bss-skills
claude plugin update apply-v2@bss-skills
```

## Notes

- `docsmith` is for structured documentation work.
- `cloud-architect` is for cloud design, migration, and cost/security planning.
- `apply-v2` is for UI migration work in the FPT Cloud console where v1 and v2 coexist at runtime.

## License

MIT
