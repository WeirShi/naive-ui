# 东西 Thing

当你想要描述一个东西，使用 Thing。如果你觉得这个组件不能满足你的需求，可以自己写一个。

我其实很想把所有常用的布局都装到一个组件里，我想了很久，感觉这个组件确实已经存在了，那就是浏览器本身。

## 演示

```demo
basic
indent
```

## Props

| 名称             | 类型      | 默认值      | 说明             |
| ---------------- | --------- | ----------- | ---------------- |
| content-indented | `boolean` | `false`     | 是否启用内容缩进 |
| content          | `string`  | `undefined` | 内容区域         |
| description      | `string`  | `undefined` | 描述信息         |
| title-extra      | `string`  | `undefined` | 标题的附加信息   |
| title            | `string`  | `undefined` | 标题             |

## Slots

| 名称         | 参数 | 说明           |
| ------------ | ---- | -------------- |
| action       | `()` | 操作区域插槽   |
| default      | `()` | 内容信息       |
| description  | `()` | 描述信息       |
| header-extra | `()` | 头部的附加信息 |
| header       | `()` | 头部信息       |
