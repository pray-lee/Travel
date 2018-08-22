<template>
  <div class="container" @click="handleGallaryClick">
    <div class="wrapper">
      <swiper :options="swiperOption">
        <!-- slides -->
        <swiper-slide v-for="(img, index) of imgs" :key="index">
          <img class="swiper-img"
               :src="img"
               alt=""/>
        </swiper-slide>
        <!-- Optional controls -->
        <div class="swiper-pagination" slot="pagination"></div>
      </swiper>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'CommonGallery',
    props: {
      imgs: {
        type: Array,
        default () {
          return [
            'http://img1.qunarzz.com/sight/p0/1603/60/6020660bc5fc5c7d90.water.jpg_r_800x800_910172f1.jpg',
            'http://img1.qunarzz.com/sight/p0/1603/60/6020660bc5fc5c7d90.water.jpg_r_800x800_910172f1.jpg'
          ]
        }
      }
    },
    data () {
      return {
        swiperOption: {
          pagination: '.swiper-pagination',
          paginationType: 'fraction',
          loop: true,
          observeParents: true,
          observer: true
        }
      }
    },
    methods: {
      handleGallaryClick () {
        this.$emit('close')
      }
    }
  }
</script>

<style lang="stylus" scoped>
  .container >>> .swiper-container
    overflow:inherit
  .container
    display: flex
    flex-direction: column
    justify-content: center
    z-index: 999
    position: fixed
    top: 0
    right: 0
    left: 0
    bottom: 0
    background: #000
    .wrapper
      background: #fff
      text-align: center
      .swiper-pagination
        color: #fff
        bottom: -1rem
      .swiper-img
        width:100%
</style>
