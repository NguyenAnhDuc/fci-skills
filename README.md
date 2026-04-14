# FCI Skills

Skills repo for FCI teams.

## Available skills

| Skill | Command | Purpose |
| --- | --- | --- |
| [Docsmith](plugins/docsmith/) | `/fci/docsmith` | Documentation workflow |
| [Apply V2](plugins/apply-v2/) | `/fci/apply-v2` | Migrate Material-UI v1 pages to FCI Design System v2 |

## Install

```bash
claude plugin marketplace add https://github.com/NguyenAnhDuc/fci-skills.git
claude plugin install docsmith@fci-skills
claude plugin install apply-v2@fci-skills
/reload-plugins
```

## Update

```bash
claude plugin marketplace update fci-skills
claude plugin update docsmith@fci-skills
claude plugin update apply-v2@fci-skills
```

## Notes

- `docsmith` is for structured documentation work.
- `apply-v2` is for UI migration work where v1 and v2 coexist at runtime.

## License

MIT
