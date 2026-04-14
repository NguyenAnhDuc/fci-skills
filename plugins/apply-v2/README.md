# Apply V2

Use this skill when migrating an existing Material-UI (v1) page to the FCI Design System (v2) in the FPT Cloud console.

The migration model assumes v1 and v2 coexist at runtime and rendering is controlled by `useLayout()` and `isApplyingV2`.

## Install

```bash
/plugin marketplace add https://github.com/NguyenAnhDuc/bss-skills.git
/plugin install apply-v2@bss-skills
/reload-plugins
```

## Usage

```text
/fci/apply-v2 migrate vpn list page to v2
/fci/apply-v2 convert custom-image create page
/fci/apply-v2 apply v2 for security-group detail page
```

## What this skill covers

- registering routes in `V2_READY_PAGES`
- replacing direct MUI imports with `useLayout().components`
- wrapping the page with `PageWrapper`
- migrating tables, forms, dialogs, empty states, and tutorials
- avoiding common v1/v2 coexistence mistakes

## References included

- `references/tables.md`
- `references/forms.md`
- `references/detail-pages.md`
- `references/dialogs.md`
- `references/tutorials.md`

## Notes

This skill is opinionated around the current FPT Cloud console structure, especially:
- `layouts/LayoutProvider`
- `layouts/PageWrapper`
- `components/FCIApdater`
- `components/SimpleTableV3`

If the underlying layout system changes, update the references before relying on it for large migrations.

## License

MIT
