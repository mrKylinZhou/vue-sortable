<template>
  <div ref="wrapper">
    <div class="item">1</div>
    <div class="item">2</div>
    <div class="item">3</div>
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
      sortable: null
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
        draggable: '.item',
        delay: 0,
        animation: 150
      });
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
