# vue-sortable

> 一个基于Vue的排序组件
> 基于@shopify/draggable开发

已经有很多基于vue开发的排序组件了，但绝大部分的拖拽都是依赖于原生drag。
基于原生拖拽的组件都有一个非常不好的体验，因为拖拽中的样式永远都是一个矩形的Dom快照
拖拽中的样式常常会匪夷所思

@shopify/draggable 是一个非常出色的拖拽库，它拖拽和排序时提供的是一个真实dom的拷贝。

很可惜的是@shopify/draggable并没有直接提供一个可用的vue版本，vue-sortable做的就是这个事情。

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
