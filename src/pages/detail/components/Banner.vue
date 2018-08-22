<template>
  <div>
    <div class="banner" @click="handleBannerClick">
      <img class="banner-img" src="https://img1.qunarzz.com/sight/p0/201311/12/3e2de7e7f2fa170fc8d65eac.jpg_600x330_c73533f8.jpg" alt="">
      <div class="banner-info">
        <div class="banner-title">
          测试标题
        </div>
        <div class="banner-number">
            <span class="iconfont banner-icon">&#xe632;</span>
            49
        </div>
      </div>
    </div>
    <fade-animation>
      <common-gallery :imgs="imgs" v-show="showGallary" @close="handleGallaryClose"></common-gallery>
    </fade-animation>
  </div>

</template>
<script>
  import CommonGallery from 'common/gallery/Gallery'
  import FadeAnimation from 'common/fade/Fade'
  export default {
    name: 'DetailBanner',
    components: {
      CommonGallery,
      FadeAnimation
    },
    computed: {

    },
    methods: {
      handleBannerClick () {
        this.showGallary = true
      },
      handleGallaryClose () {
        this.showGallary = false
      }
    },
    data () {
      return {
        showGallary: false,
        imgs: [
          'http://img1.qunarzz.com/sight/p0/1603/60/6020660bc5fc5c7d90.water.jpg_r_800x800_910172f1.jpg',
          'http://img1.qunarzz.com/sight/p0/1603/60/6020660bc5fc5c7d90.water.jpg_r_800x800_910172f1.jpg',
          'http://img1.qunarzz.com/sight/p0/1603/60/6020660bc5fc5c7d90.water.jpg_r_800x800_910172f1.jpg'
        ]
      }
    }
  }
</script>
<style lang="stylus" scoped>
  .banner
    position:relative
    overflow: hidden
    height: 0
    padding-bottom: 55%
    .banner-img
      width: 100%
    .banner-info
      display: flex
      position: absolute
      left:0
      right:0
      bottom:0
      line-height: .6rem
      color: #fff
      .banner-title
        flex:1
        font-size: .32rem
        padding: 0 .2rem
      .banner-number
        margin-top: .14rem
        padding: 0 .4rem
        height: .32rem
        line-height: .32rem
        border-radius: .2rem
        background: rgba(0,0,0,.6)
        font-size: .24rem
        .banner-icon
          font-size: .24rem
</style>
