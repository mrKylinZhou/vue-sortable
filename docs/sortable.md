## Sortable

### 简单的例子

```html
<sortable
  v-model="lists"
  @sorted="sorted">
  <div slot-scope="props">
    {{ props.data }}
  </div>
</sortable>
```

### 属性
| 参数      | 说明          | 类型      | 可选值                           | 默认值  |
|---------- |-------------- |---------- |--------------------------------  |-------- |
| value | 完整的列表 | array | — | — |
| delay | 延迟时间 | number | — | 300 |
| disabled | 是否禁止使用功能 | boolean | — | false |
| wrapClass | 附加的包裹容器的类名 | string | — | - |
| itemCLass | 附加的每一个Item的类名 | string | — | - |

### items
| 参数      | 说明          | 类型      | 可选值                           | 默认值  |
|---------- |-------------- |---------- |--------------------------------  |-------- |
| key | value每一项必须要包含的属性（每一项均不可重复 且尽量不要使用index） | string/number | — | — |

```javascript

const lists = [
  { key: 1, value: 1 },
  { key: 2, value: 2 }
]

export default {
  data() {
    return {
      lists: lists
    }
  }
}

```

### 时间
| 事件名称 | 说明 | 回调参数 |
|---------- |-------- |---------- |
| sorted | 排序完成 | value |
