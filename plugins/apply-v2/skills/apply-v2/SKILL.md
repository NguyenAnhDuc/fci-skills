---
name: apply-v2
description: Migrate an existing Material-UI (v1) page to the FCI Design System (v2). Both versions coexist at runtime — the active version is driven by `isApplyingV2` from `useLayout()`. Invoke when the task involves: `apply v2`, `migrate to v2`, `convert to v2`, `useLayout`, `isApplyingV2`, `V2_READY_PAGES`, `PageWrapper`, MUI-to-FCI migration, or "new UI".
---

## Description

## Trigger

## How It Works

```
isApplyingV2 = (isNewUI && pageIsV2Ready) || (!isNewUI && pageIsV1Ready)
```

- `isNewUI` — `localStorage.getItem('isNewUI')`
- `pageIsV2Ready` — route listed in `V2_READY_PAGES` in `constants.js`
- `isApplyingV2` — from `useLayout()`, drives all rendering decisions

## Core Files

| File                                  | Role                                                       |
| ------------------------------------- | ---------------------------------------------------------- |
| `layouts/LayoutProvider/index.js`     | Context provider, V1/V2 component maps, `useLayout()` hook |
| `layouts/LayoutProvider/constants.js` | `V2_READY_PAGES` / `V1_READY_PAGES` route arrays           |
| `layouts/PageWrapper.js`              | Universal page template                                    |
| `components/FCIApdater/`              | Adapter components bridging MUI to FCI props               |
| `components/SimpleTableV3/`           | V2 table (wraps FCI Table organism)                        |
| `components/empty/FciEmpty.js`        | V2 empty state (wraps FCI StatusCard)                      |

## Reference Implementation

Full feature implemented in v2 (list + detail + create): `pages/vpn`. For additional examples: `security-group`, `custom-image`, `schedule`.

## Component Map (V1 to V2)

`useLayout().components` resolves automatically. Key entries:

| Key                                                      | V1                          | V2                             |
| -------------------------------------------------------- | --------------------------- | ------------------------------ |
| `Button`, `Box`, `Typography`, `Link`, `Chip`, `Divider` | MUI                         | FCI equivalents                |
| `SimpleTable`                                            | SimpleTableV2 (react-table) | SimpleTableV3 (FCI Table)      |
| `Empty`                                                  | BaseEmpty                   | FciEmpty (StatusCard)          |
| `Tabs` / `Tab`                                           | MUI                         | FCI                            |
| `Input` / `InputField`                                   | InputField                  | FciInputAdapter / InputFieldV2 |
| `Select`                                                 | AsyncSelectField            | FciSelectAdapter               |
| `Textarea`                                               | TextArea                    | FciTextareaAdapter             |
| `MultiSelect`                                            | AsyncSelectField            | FciMultiSelectAdapter          |
| `CheckBoxField`                                          | CheckBoxField               | FciCheckBoxAdapter             |
| `AutoCompleteField`                                      | AsyncSelectField            | AutocompleteAdapter            |
| `SimpleSelect`                                           | Select                      | SelectV2                       |
| `SearchableSelect`                                       | AsyncSelectField            | SearchableSingleSelect         |
| `RadioGroup`                                             | RadioGroup                  | FciRadioGroup                  |
| `ChipGroup`                                              | TagsRow                     | FCI ChipGroup                  |
| `Stepper`                                                | MUI Stepper                 | FCI Stepper                    |
| `IconButton` / `IconTooltip`                             | MUI                         | FCI equivalents                |
| `DateTimePicker`                                         | DateTimePicker              | FCI DateTimePicker             |
| `CustomDialog` / `FormModal`                             | CustomDialog                | FormModalAdapter               |
| `ConfirmationModal` / `InfoModal`                        | CustomDialog                | FCI equivalents                |
| `ContentGroup`, `HelpText`, `TextContent`, `TextTitle`   | Typography                  | FCI equivalents                |
| `Flex`, `ListEmpty`                                      | null / EmptyState           | Flex / EmptyStateV3            |

Full maps: `LayoutProvider/index.js` lines 174-274.

---

## Migration Steps (Core)

### Step 1 — Read the target page

Understand: current imports, page structure (list / detail / form), URL constants, routing, data fetching.

### Step 2 — Register routes in `V2_READY_PAGES`

```js
// layouts/LayoutProvider/constants.js
import { myFeatureUrls } from "../../routes/urls";

const V2_READY_PAGES = [
  myFeatureUrls.list,
  myFeatureUrls.create,
  myFeatureUrls.detail,
  myFeatureUrls.edit,
];
```

Register **every** route for the feature. Missing one causes a jarring v1/v2 flash mid-navigation.

### Step 3 — Add `useLayout()` and pull versioned components

```js
// BEFORE
import { Box, Button, Typography } from "@material-ui/core";
import SimpleTable from "../../components/SimpleTableV2";

// AFTER
import { useLayout } from "../../layouts/LayoutProvider/index";

const MyPage = () => {
  const { components, isApplyingV2 } = useLayout();
  const { Box, Button, Typography, SimpleTable } = components;
  // ...
};
```

- Only destructure what you use
- Remove old direct MUI imports now provided by `components`
- Keep non-UI imports (hooks, utilities, constants) as-is

### Step 4 — Wrap with `PageWrapper`

```js
import PageWrapper from "../../layouts/PageWrapper";
import { PlusIcon } from "@fci-ui/ui/build/v2/icons";

return (
  <PageWrapper
    HeaderProps={{
      title: "My Feature",
      subtitle: "Manage your features",
      breadcrumbs: !isApplyingV2 && [{ name: "Parent", path: parentUrl }],
      actions: (
        <Button
          variant="contained"
          color="primary"
          startIcon={isApplyingV2 && <PlusIcon />}
        >
          Create
        </Button>
      ),
      tabs: <MyTabs />,
    }}
    Tutorial={() => <MyTutorial />}
    Notification={() => <MyNotification />}
  >
    {/* page content */}
  </PageWrapper>
);
```

**PageWrapper props:**

| Prop                                                             | Type        | Description                                     |
| ---------------------------------------------------------------- | ----------- | ----------------------------------------------- |
| `HeaderProps`                                                    | object      | `{title, subtitle, breadcrumbs, actions, tabs}` |
| `Tutorial`                                                       | elementType | Rendered below content                          |
| `Notification`                                                   | elementType | Rendered above content                          |
| `isDisabledPaperContent`                                         | bool        | Use Box instead of Paper for children           |
| `ContainerProps` / `ContainerContentProps` / `ContentPaperProps` | object      | Outer layout overrides                          |

**Breadcrumbs:** list pages -> hide in v2 (`!isApplyingV2 && [...]`). Detail/create pages -> keep for back-nav.

---

## Implementation References

Read these only when implementing the specific page type:

| Reference                                                  | When to read                                                                 |
| ---------------------------------------------------------- | ---------------------------------------------------------------------------- |
| [references/tables.md](./references/tables.md)             | Migrating list pages — table columns, empty states                           |
| [references/forms.md](./references/forms.md)               | Migrating create/update forms — form fields, table-form (FieldArray) pattern |
| [references/detail-pages.md](./references/detail-pages.md) | Migrating detail pages                                                       |
| [references/dialogs.md](./references/dialogs.md)           | Migrating dialogs (confirm, form modals, info modals)                        |
| [references/tutorials.md](./references/tutorials.md)       | Adding tutorials / QuickGuide to a page                                      |

---

## Migration Checklist

- [ ] All page URLs added to `V2_READY_PAGES` in `constants.js`
- [ ] URL constants imported in `constants.js`
- [ ] `const {components, isApplyingV2} = useLayout()` added to page
- [ ] Direct MUI imports replaced by `components` destructuring
- [ ] Page wrapped with `PageWrapper` + `HeaderProps`
- [ ] Breadcrumbs hidden on list pages, shown on detail/create pages
- [ ] Table columns: both V1 (`Header/accessor`) and V2 (`title/render/field`) formats provided
- [ ] Empty state uses `components.Empty`
- [ ] Tutorial uses `QuickGuide`, wired as `Tutorial={() => <MyTutorial />}`
- [ ] Form fields use `component={Input}` from `useLayout()`
- [ ] V2 actions use FCI icons from `@fci-ui/ui/build/v2/icons`
- [ ] Dialogs use `components.CustomDialog`
- [ ] If list page, implemented filter v2 if filter exists in v1

## Common Pitfalls

1. **Forgot to register route** — `isApplyingV2` stays `false`. Always check `constants.js` first.
2. **Double Paper wrapping** — `PageWrapper` wraps children in Paper by default. Use `isDisabledPaperContent={true}` for Box.
3. **Direct MUI import bypasses version switching** — Always use `components.Button`, not `import {Button} from '@material-ui/core'`.
4. **Wrong column schema** — `Header/accessor` won't work with SimpleTableV3. Use `title/render/field`.
5. **Missing adapter** — Check `components/FCIApdater/` before writing a custom bridge.
6. **Tutorial as element vs elementType** — Use `Tutorial={() => <MyGuide />}` not `Tutorial={<MyGuide />}`.
7. **Icon prop types** — `iconV2` expects a component reference (`PlusIcon`), not JSX (`<PlusIcon />`).
