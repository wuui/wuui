<template lang="pug">
  .main
    main-nav
    .main__content.clearfix
      wu-row
        wu-col(:span="4")
          side-bar(v-on:data="inactive")
        wu-col(:span="20")
          .main__container
            router-view
    main-footer
</template>

<script>
  import $ from 'jquery'
  import mainNav from '@/components/base/head'
  import sideBar from '@/components/base/sidebar'
  import mainFooter from '@/components/base/footer'
  export default {
    data () {
      return {
        show: true // 页签数据
      }
    },
    components: {
      mainNav,
      sideBar,
      mainFooter
    },
    created () {
      // console.log(this.show)
    },
    methods: {
      inactive (data) {
        let width = data
        $('.main__container').animate({left: width + 'px'})
        $('.sidebar').animate({width: width + 'px'})
      }
    }
  }
</script>

<style lang="stylus">
  @import "./css/index.styl"
  .main
    background #ececec
  .main__content
    display block
    margin 0 48px
    border-radius 4px
    padding 1px 0 0
    margin-bottom 24px
    background  #fff
    height 100%
    .tab__container
      padding 0 20px
      background #F9FAFC
      height 32px
      overflow hidden
      .tab__item
        display inline-block
        width 150px
        height 32px
        color #666
        line-height 32px
        text-align center
        background #b4d1ee
        &--active
          background #e7eef3
        .el-icon-close
          font-size 8px
          font-weight 200
    .sidebar
      display block
      border-right 1px solid #e9e9e9
    .main__container
      display block
      min-height 500px
      overflow hidden
  footer
    clear both
    font-size 12px
    background #fff
    position relative
    z-index 1
    color rgba(0,0,0,.65)
    box-shadow 0 1000px 0 1000px #fff
    .container
      padding 20px 50px
      margin 0 auto
      background #EFF2F7
      .footer-main .footer-main-title
        line-height 1
        font-size 22px
        margin 0
</style>
