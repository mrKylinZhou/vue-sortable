<template>
  <div ref="wrapper">
    <div
      class="k-sortable-item"
      v-for="(item, index) in lists"
      :key="index">
      {{ item }}
    </div>
  </div>
</template>

<script>
import { Sortable } from '@shopify/draggable'

export default {
  name: 'VueSortable',
  props: {
    // 是否启动拖动
    canSort: {
      type: Boolean,
      default: true
    }
  },
  data() {
    return {
      sortable: null,
      lists: new Array(30).fill('t').map((item, index) => item + index)
    }
  },
  watch: {
    canSort(sort) {
      sort
        ?  this.init()
        : this.destroy()
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
      })
    },
    destroy() {
      this.sortable && this.sortable.destroy()
      this.sortable = null
    }
  },
  mounted() {
    this.$nextTick(() => {
      this.canSort && this.init()
    })
  },
  destroyed() {
    this.destroy()
  }
}
</script>

<style>
  * {
    outline: none;
  }
</style>
