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

### 时间
| 事件名称 | 说明 | 回调参数 |
|---------- |-------- |---------- |
| sorted | 排序完成 | value |
