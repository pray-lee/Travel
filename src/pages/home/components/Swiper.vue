<template>
	<div class="wrapper">
		<swiper :options="swiperOption" ref="mySwiper" v-if="showSwiper">
	    	<!-- slides -->
		    <swiper-slide v-for="item of swiperList" :key="item.id">
		    	<img class="swiper-img" :src="item.imgUrl" alt="">
		    </swiper-slide>
		    <!-- Optional controls -->
		    <div class="swiper-pagination"  slot="pagination"></div>
		  </swiper>
	</div>
</template>
<script type="text/javascript">
	export default {
		name: 'HomeSwiper',
		props: {
			swiperList: Array
		},
		data() {
			return {
				swiperOption: {
					pagination: '.swiper-pagination',
					loop: true
				},
			}
		},
		computed: {
			showSwiper() {
				return this.swiperList.length
			}
		}
	}
</script>
<style lang="stylus" scoped>
	// >>> 这个是穿透的意思。如果引用了外部的组件。这个符号可以穿透当前的scoped的css作用域。因为.swiper-pagination-bullet-active是swiper插件的css样式，所以我们要穿透出去，当前的样式代码才会生效
	.wrapper >>> .swiper-pagination-bullet-active
		background: #fff !important
	.wrapper
		overflow: hidden
		width: 100%
		height:0
		padding-bottom: 26.67%
	.swiper-img
		width: 100%		
</style>