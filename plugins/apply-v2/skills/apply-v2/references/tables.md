# Reference: Tables

> Read this when migrating **list pages / tables**.

For V2, `SimpleTable` resolves to `SimpleTableV3`, so columns must support the V2 schema.

Rules:
- Keep server-side fetching / pagination logic unchanged initially
- Replace only rendering contract first
- Ensure empty state uses `components.Empty`
- Preserve row actions, bulk actions, and filters
- If supporting both versions in one page, define columns carefully so V1/V2 both render correctly when needed

Typical V2 fields:
- `title`
- `field`
- `render`

Typical V1 fields:
- `Header`
- `accessor`

Verify sorting, filtering, and row click behavior after migration.
