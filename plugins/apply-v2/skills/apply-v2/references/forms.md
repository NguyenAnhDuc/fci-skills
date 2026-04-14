# Reference: Forms

> Read this when migrating **create/update pages** with forms.

## Form Components

```js
import { Field, reduxForm } from 'redux-form'

const useStyles = makeStyles(() => ({
  formContainer: {
    display: 'flex',
    flexDirection: 'column',
    gap: '24px',
  },
}))

const MyForm = ({ handleSubmit, submitting }) => {
  const { components, isApplyingV2 } = useLayout()
  const { Input, Select, Textarea, Button } = components
  const classes = useStyles()

  return (
    <form onSubmit={handleSubmit} className={isApplyingV2 && classes.formContainer}>
      <Field naked label="Title:" name="title" component={Input} placeholder="Enter title" required />
      <Field naked label="Category:" name="category" component={Select} options={[{ label: 'Option A', value: 'a' }]} placeholder="Select category" />
      <Field naked label="Description:" name="description" component={Textarea} rows={4} />
      <Button type="submit" variant="contained" color="primary" disabled={submitting}>
        Submit
      </Button>
    </form>
  )
}
export default reduxForm({ form: 'myForm' })(MyForm)
```

Key rules:
- Pass `component={Input}` from `useLayout()` — not a direct import
- `naked` strips default wrapper styling
- Adapters handle `meta.touched/error/submitFailed` automatically
- Select `options`: `[{label, value}]` — works for both versions

## Table-Form Pattern (FieldArray in table rows)

When form rows are rendered as a table, use MUI Table structure + FCI table styles:

```js
import Table from '@material-ui/core/Table'
import TableBody from '@material-ui/core/TableBody'
import TableCell from '@material-ui/core/TableCell'
import TableContainer from '@material-ui/core/TableContainer'
import TableHead from '@material-ui/core/TableHead'
import TableRow from '@material-ui/core/TableRow'
import useTableStyles from '@fci-ui/ui/build/organisms/Table/styles'
import { Box } from '@fci-ui/ui/build/atoms'
import classNames from 'classnames'

const TableFormFields = ({ fields }) => {
  const { components } = useLayout()
  const { Button, Input, Select } = components
  const tableClasses = useTableStyles()

  return (
    <TableContainer
      component={Box}
      className={classNames(
        tableClasses.container,
        tableClasses.borderEdge,
        tableClasses.highlightRow,
        tableClasses.borderCell,
      )}
    >
      <Table>
        <TableHead>
          <TableRow>
            <TableCell><strong>Type</strong></TableCell>
            <TableCell><strong>Quantity</strong></TableCell>
            <TableCell><strong>Actions</strong></TableCell>
          </TableRow>
        </TableHead>
        <TableBody>
          {fields.map((name, index) => (
            <TableRow key={name}>
              <TableCell>
                <Field naked name={`${name}.type`} component={Select} options={typeOptions} />
              </TableCell>
              <TableCell>
                <Field naked name={`${name}.quantity`} component={Input} type="number" />
              </TableCell>
              <TableCell>
                <Button color="secondary" onClick={() => fields.remove(index)}>Remove</Button>
              </TableCell>
            </TableRow>
          ))}
          <TableRow>
            <TableCell colSpan={3}>
              <Button variant="text" onClick={() => fields.push({})}>+ Add Item</Button>
            </TableCell>
          </TableRow>
        </TableBody>
      </Table>
    </TableContainer>
  )
}

// In the parent form:
<FieldArray name="items" component={TableFormFields} />
```

If v1/v2 layouts differ significantly, create separate components and switch:

```js
const DetailComponent = isApplyingV2 ? TableFormFieldsV2 : TableFormFieldsV1
<FieldArray name="items" component={DetailComponent} />
```
