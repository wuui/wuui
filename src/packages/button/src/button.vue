<template lang="pug">
  button(:class="classes")
    Icon(class="" type="loading" v-if="loading")
    Icon(:type="icon" v-if="icon && !loading")
    span(v-if="$slots.default")
      slot
</template>

<script>
const prefixCls = 'wu-btn'
export default {
  name: 'WuButton',

  componentName: 'WuButton',

  props: {
    type: String,
    shape: String,
    htmlType: {
      type: String,
      default: 'button'
    },
    loading: Boolean,
    className: String,
    icon: String,
    ghost: {
      type: Boolean,
      default: false
    },
    size: {
      type: String,
      default: 'default'
    }
  },

  computed: {
    classes () {
      let sizeCls = ''
      switch (this.size) {
        case 'large':
          sizeCls = 'lg'
          break
        case 'small':
          sizeCls = 'sm'
      }
      return {
        [`${prefixCls}`]: true,
        [`${prefixCls}-${this.type}`]: this.type,
        [`${prefixCls}-${this.shape}`]: this.shape,
        [`${prefixCls}-${sizeCls}`]: sizeCls,
        [`${prefixCls}-icon-only`]: !this.icon && !this.loading,
        [`${prefixCls}-loading`]: this.loading,
//        [`${prefixCls}-clicked`]: this.clicked,
        [`${prefixCls}-background-ghost`]: this.ghost,
        [`${this.className}`]: !!this.className
      }
    }
  }
}
</script>
