<template>
  <div>
    <router-link tag="div" class="header-abs" to="/" v-show="showAbs">
      <span class="iconfont header-abs-back">&#xe624;</span>
    </router-link>
    <div class="header-fixed" v-show="!showAbs" :style="opacityStyle">
      风景详情
      <router-link to="/">
        <div class="iconfont header-fixed-back">&#xe624;</div>
      </router-link>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'DetailHeader',
    data () {
      return {
        showAbs: true,
        opacityStyle: {
          opacity: 0
        }
      }
    },
    methods: {
      handleScroll () {
        const top = document.documentElement.scrollTop
        if (top && top > 60) {
          let opacity = top / 140
          opacity = opacity > 1 ? 1 : opacity
          this.opacityStyle = { opacity }
          this.showAbs = false
        }else{
          this.showAbs = true
        }
      }
    },
    activated () {
      window.addEventListener('scroll', this.handleScroll, false)
    },
    deactivated () {
      window.removeEventListener('scroll', this.handleScroll, false)
    }
  }
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl'
  .header-abs
    position: absolute
    top: .2rem
    left: .2rem
    width: .8rem
    height: .8rem
    line-height: .8rem
    text-align: center
    border-radius: .4rem
    background: rgba(0, 0, 0, .8)
    .header-abs-back
      color: #ffffff
      font-size: .4rem
  .header-fixed
    position: fixed
    z-index: 2
    top:0
    left:0
    right:0
    height: $headerHeight
    line-height: $headerHeight
    text-align:	center
    color: #fff
    background: $bgColor
    font-size: .32rem
  .header-fixed-back
    position:absolute
    top:0
    left:0
    width: .64rem
    text-align:center
    font-size: .4rem
    color: #fff
</style>
