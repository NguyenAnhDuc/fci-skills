# Reference: Dialogs

> Read this when migrating **dialogs / modals**.

Use `components.CustomDialog` / `components.FormModal` from `useLayout()` instead of direct MUI dialog imports so runtime V1/V2 switching stays intact.

Rules:
- Keep open/close state and business logic unchanged
- Replace only the dialog shell first
- Use mapped buttons/icons from `components`
- Verify footer actions and spacing in both V1 and V2
- For confirmation flows, prefer the shared confirmation modal when available
