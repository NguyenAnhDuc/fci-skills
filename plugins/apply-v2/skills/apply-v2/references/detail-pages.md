# Reference: Detail Pages

> Read this when migrating **detail / show pages** to V2.

Use `PageWrapper` with breadcrumbs for back-navigation, and render read-only fields using versioned layout components from `useLayout()`.

Typical migration checklist:
- Keep breadcrumbs on detail pages
- Replace direct MUI primitives with `components.*`
- Group information blocks consistently
- Use V2 cards/content wrappers only through mapped components if possible
- Keep actions aligned in `HeaderProps.actions`

When the page mixes summary + related tables/forms, migrate shell first, then inner sections one by one.
