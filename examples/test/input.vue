<template lang="pug">
  .page
    .demo-content
      wu-input(placeholder="large" size="large")
      wu-input(placeholder="default")
      wu-input(placeholder="small" size="small")
    .demo-content
      wu-input(v-model="input")
        template(slot="addonBefore") http://
        template(slot="addonAfter") .com
      wu-input
        template(slot="addonAfter") .com
</template>

<script>
  export default {
    data () {
      return {
        input: ''
      }
    },
    watch: {
      input (newVal, oldVal) {
        console.log(newVal)
      }
    },
    methods: {
    }
  }
</script>

<style lang="stylus">
  .wu-input, .wu-input-group-wrapper
    margin-bottom 10px
</style>
