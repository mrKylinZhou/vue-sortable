<template>
  <div
    ref="wrapper"
    class="wrapper">
    <div
      class="k-sortable-item"
      v-for="(item, index) in lists"
      :key="index">
      <slot :data="item"></slot>
    </div>
  </div>
</template>

<script>
import { Sortable } from '@shopify/draggable'

import { cloneDeep } from 'lodash/lang'

export default {
  name: 'VueSortable',
  props: {
    value: {
      required: true,
      type: Array
    },
    // 是否禁止拖动
    disabled: {
      type: Boolean,
      default: false
    }
  },
  data() {
    return {
      sortable: null,
      lists: cloneDeep(this.value)
    }
  },
  watch: {
    disabled(bool) {
      bool
        ? this.destroy()
        : this.init()
    }
  },
  methods: {
    init() {
      const wrapper = this.$refs.wrapper
      if (!wrapper) return
      this.sortable = new Sortable(wrapper, {
        draggable: '.k-sortable-item',
        delay: 300
      })
      this.sortable.on('sortable:start', e => {
        e.data.dragEvent.data.mirror.style.zIndex = 200
        e.data.dragEvent.data.source.style.visibility = 'hidden'
      })
      this.sortable.on('sortable:stop', e => {
        const oldIndex = e.data.oldIndex
        const newIndex = e.data.newIndex
        const spliceItem = this.value.splice(oldIndex, 1)[0]
        this.value.splice(newIndex, 0, spliceItem)
        const v = cloneDeep(this.value)
        this.$emit('sorted', v)
        this.$emit('input', v)
      })
    },
    destroy() {
      this.sortable && this.sortable.destroy()
      this.sortable = null
    }
  },
  mounted() {
    this.$nextTick(() => {
      !this.disabled && this.init()
    })
  },
  destroyed() {
    this.destroy()
  }
}
</script>

<style scoped>
  .wrapper, .k-sortable-item {
    outline: none;
  }
</style>
