# Message

Oracle from the top(always) of the browser.

<n-space vertical>
<n-alert title="Prerequisite" type="warning">
  If you want use message, you need to wrap the component where you call related methods inside <n-text code>n-message-provider</n-text> and use <n-text code>useMessage</n-text> to get the API.
</n-alert>
For example:

```html
<!-- App.vue -->
<n-message-provider>
  <content />
</n-message-provider>
```

```js
import { useMessage } from 'naive-ui'

// content
export default {
  setup () {
    const message = useMessage()
    return {
      warning () {
        message.warning('...')
      }
    }
  }
}
```

</n-space>

## Demos

```demo
basic
icon
timing
closable
modify-content
manually-close
about-theme
multiple-line
```

## API

### MessageProvider Props

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| duration | `number` | `3000` | All messages's default duration. |
| max | `number` | `undefined` | Limit the number of message to display. |
| to | `string \| HTMLElement` | `'body'` | Container node of message container. |

### MessageProvider Injection API

#### MessageProvider Injection Methods

| Name | Type | Description |
| --- | --- | --- |
| error | `(content: string \| (() => VNodeChild), option?: MessageOption) => MessageReactive` | Use error type message. |
| info | `(content: string \| (() => VNodeChild), option?: MessageOption) => MessageReactive` | Use info type message. |
| loading | `(content: string \| (() => VNodeChild), option?: MessageOption) => MessageReactive` | Use loading type message. |
| success | `(content: string \| (() => VNodeChild), option?: MessageOption) => MessageReactive` | Use success type message. |
| warning | `(content: string \| (() => VNodeChild), option?: MessageOption) => MessageReactive` | Use warning type message. |

#### MessageOption Properties

| Name         | Type          | Description                               |
| ------------ | ------------- | ----------------------------------------- |
| closable     | `boolean`     | Whether to show close icon.               |
| duration     | `number`      | The duration of the message.              |
| icon         | `() => VNode` | Message icon.                             |
| onAfterLeave | `() => void`  | Callback after message disappeared.       |
| onClose      | `() => void`  | Callback when close icon is clicked.      |
| onLeave      | `() => void`  | Callback when message start to disappear. |

#### MessageReactive Properties

| Name | Type | Description |
| --- | --- | --- |
| closable | `boolean` | Whether to show close icon. |
| content | `string \| (() => VNodeChild)` | Message content. |
| destory | `() => void` | Message destory method. |
| icon | `() => VNode` | Message icon. |
| type | `'info' \| 'success' \| 'warning' \| 'error' \| 'loading'` | Message type. |
| onAfterLeave | `() => void` | Callback after message disappeared. |
| onLeave | `() => void` | Callback when message start to disappear. |

#### MessageReactive Methods

| Name    | Type | Description             |
| ------- | ---- | ----------------------- |
| destroy | `()` | Message destory method. |

## Q & A

### Use Message Outside Setup

<n-space vertical>
<n-alert type="warning">
  You need to mount the return value of <n-text code>useMessage</n-text> to the window in the top-level setup and then call it. Before calling it, you need to make sure that message has been mounted successfully.
</n-alert>

```html
<!-- App.vue -->
<n-message-provider>
  <content />
</n-message-provider>
```

```html
<!-- content.vue -->
<template>...</template>

<script>
  import { useMessage } from 'naive-ui'

  // content
  export default {
    setup() {
      window.$message = useMessage()
    }
  }
</script>
```

```js
// xxx.js
export const handler = () => {
  // You need to ensure that window.$message = message has been executed in setup
  window.$message.success(
    'Cause you walked hand in hand With another man in my place'
  )
}
```

</n-space>
