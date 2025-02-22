---
title: Group Field
prev: /docs/fields/toggle
next: /docs/fields/group-list
consumes:
  - file: /packages/tinacms/src/plugins/fields/GroupFieldPlugin.tsx
    details: Shows group field interface and how to use
---

The `group` field represents a group of values. This field is typically used with an array of objects within a json file or nested frontmatter values in a markdown file.

## Definition

Below is an example of how a `group` field could be defined in a Gatsby json form. Read more on passing in json form field options [here](/docs/gatsby/json#customizing-json-forms).

If the json for some example contact info looked like this:

```json
{
  "contact": {
    "email": "hello@tinacms.org",
    "twitter_handle": "tina_cms",
    "github_handle": "tinacms"
  },
}
```

Our form options would look like this:

```javascript
const formOptions = {
    label: 'Info Page',
    fields: [
      {
        label:"Contact Info",
        name:"rawJson.contact",
        description: "Contact info",
        component: "group",
        fields: [
          {
            label:"Email",
            name:"email",
            description: "Contact email",
            component: "text"
          },
          { label:"Twitter",
            name:"twitter_handle",
            description: "Twitter handle",
            component: "text"
          },
          { label:"Github",
            name:"github_handle",
            description: "Github username",
            component: "text"
          }
        ]
      },
      //...
    ]
  }
```

## Options

 - `name`: The path to some value in the data being edited.
 - `component`: The name of the React component that should be used to edit this field. Available field component types are [defined here](/docs/concepts/fields#field-types)
 - `label`: A human readable label for the field. This label displays in the sidebar and is optional. If no label is provided, the sidebar will default to the name.
 - `fields`: An array of group values that will render as a sub-menu.

```typescript
import { Field } from '@tinacms/core'

interface GroupConfig {
  name: string
  component: 'group'
  label?: string
  fields: Field[]
}
```
