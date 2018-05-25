# vue-sortable

> A Vue.js sortable component

Only for test now! Don't use it for production

## Install
```shell
npm install vue-isortable || yarn add vue-isortable
```

## Links

- [issues](https://github.com/mrKylinZhou/vue-sortable/issues)
- [docs](./docs/sortable.md)

## Quick Start
```html
<sortable
  v-model="lists"
  @sorted="sorted">
  <div slot-scope="props">
    {{ props.data }}
  </div>
</sortable>
```

## LICENSE
MIT
