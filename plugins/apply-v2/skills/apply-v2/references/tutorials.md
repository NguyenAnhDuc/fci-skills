# Reference: Tutorials / QuickGuide

> Read this when adding a **tutorial or QuickGuide** to a page.

```js
import QuickGuide from '../../components/FCIApdater/QuickGuide'
import { PlusIcon, EyeShowIcon } from '@fci-ui/ui/build/v2/icons'

function MyTutorial() {
  return (
    <QuickGuide
      title="What you can do"
      quickGuides={[
        {
          title: 'Create item',
          subTitle: 'How to create',
          link: '/docs/create',
          iconV2: PlusIcon,
          icon: <></>,
        },
        {
          title: 'View details',
          subTitle: 'How to view',
          link: '/docs/view',
          iconV2: EyeShowIcon,
          icon: <></>,
        },
      ]}
    />
  )
}
```

- `iconV2` — component reference (not JSX), used in v2
- `icon` — JSX element, used in v1 (use `<></>` if no v1 icon)

Wire into PageWrapper: `Tutorial={() => <MyTutorial />}` (elementType, not rendered element).
