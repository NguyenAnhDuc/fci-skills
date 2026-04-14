# Docsmith

Docsmith is a documentation workflow skill based on PRC-010.

Use it when you need to plan, draft, review, and verify product documentation in a more structured way instead of writing docs ad hoc.

## Install

```bash
/plugin marketplace add https://github.com/NguyenAnhDuc/bss-skills.git
/plugin install docsmith@bss-skills
/reload-plugins
```

## Usage

```text
/fci/docsmith help
/fci/docsmith start MyProduct
/fci/docsmith draft APIEndpoint
/fci/docsmith verify MyProduct
```

## Workflow

```text
audience → plan → review-plan → sitemap → voice → draft → edit → walkthrough → peer-review → tech-review → incorporate → publish
```

## Main commands

| Command | Alias | Purpose |
| --- | --- | --- |
| help | h | Show command reference |
| start | — | Start the process |
| audience | aud | Define audience and goals |
| plan | pl | Create the documentation plan |
| review-plan | rp | Review and approve the plan |
| sitemap | sm | Define structure and navigation |
| voice | vc | Define writing standards |
| draft | dr | Draft the documentation |
| edit | ed | Run editing passes |
| walkthrough | wt | Verify docs against the product |
| validate | val | Re-run walkthrough tests only |
| test | t | Generate walkthrough test cases |
| verify | vf | Run verification checks |
| peer-review | pr | Human review |
| tech-review | tr | Optional technical review |
| incorporate | inc | Apply feedback |
| publish | pub | Final approval |

## Notes

- `start` is the safest entry point if the work is still vague.
- `draft` is useful when the structure already exists and you just need content.
- `verify` is useful as a standalone quality gate.
- `walkthrough` is for cases where the documentation needs to be checked against a live product.

## Output

Typical output goes under:

```text
docs/
├── plan/
├── standards/
├── drafts/
├── walkthrough/
└── images/
```

## References

- `skills/docsmith/SKILL.md`
- `skills/docsmith/process-reference.md`
- `skills/docsmith/tools-reference.md`

## License

MIT
