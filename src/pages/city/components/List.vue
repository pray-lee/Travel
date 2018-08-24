<template>
	<div class="list" ref="wrapper">
		<div>
			<div class="area">
				<div class="title border-topbottom">当前城市</div>
				<div class="button-list">
					<div class="button-wrapper">
						<div class="button">{{this.city}}</div>
					</div>
				</div>
			</div>
			<div class="area">
				<div class="title border-topbottom">热门城市</div>
				<div class="button-list">
					<div class="button-wrapper" v-for="item of hot" :key="item.id" @click="handleCityClick(item.name)">
						<div class="button">{{item.name}}</div>
					</div>
				</div>
			</div>
			<div class="area" v-for="(item, key) of cities" :key="key" :ref="key">
				<div class="title border-topbottom">{{key}}</div>
				<div class="button-list">
					<div class="button-wrapper" v-for="innerItem of item" :key="innerItem.id" @click="handleCityClick(innerItem.name)">
						<div class="button">{{innerItem.name}}</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</template>
<script>
	import BScroll from 'better-scroll'
	import { mapState, mapMutations } from 'vuex'
	export default {
		name: 'CityList',
		props: {
			cities: Object,
			hot: Array,
			letter: String
		},
		computed: {
			...mapState(['city'])
		},
		methods: {
			handleCityClick(city) {
			  alert(1)
			  alert(city)
				// this.$store.dispatch('changeCity', city)
				// this.$store.commit('changeCity', city)
				this.changeCity(city)
				this.$router.push('/')
			},
			...mapMutations(['changeCity'])
		},
		mounted() {
			this.scroll = new BScroll(this.$refs.wrapper)
		},
		watch: {
			letter() {
				this.scroll.scrollToElement(this.$refs[this.letter][0]);
			}
		}
	}
</script>
<style lang="stylus" scoped>
.list
	position: absolute
	top: 1.58rem
	left: 0
	bottom: 0
	right: 0
	overflow: hidden
	.border-topbottom
		&:before
			border-color: #ccc
		&:after
			border-color: #ccc
	.border-bottom
		&:before
			border-color: #ccc
	.title
		line-height: .54rem
		background: #eee
		padding-left: .26rem
		color: #666
	.button-list
		overflow: hidden
		padding: .1rem .6rem .1rem .1rem
		.button-wrapper
			float:left
			width: 33.33%
			.button
				text-align: center
				padding: .1rem 0
				margin: .1rem
				border: .02rem solid #ccc
				border-radius: .06rem
	.item-list
		.item
			line-height: .76rem
			color: #666
			padding-left: .2rem
</style>
