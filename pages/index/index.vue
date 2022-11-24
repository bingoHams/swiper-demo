<template>
	<view>
		<!-- #ifndef APP-NVUE || MP-TOUTIAO -->
		<view class="u-demo-block">
			<text class="u-demo-block__title">卡片式</text>
			<u-swiper :list="list3" previousMargin="30" :circular="false" nextMargin="30" :autoplay="false" radius="5"
				bgColor="#ffffff" @click="itemClick" :current="currentIndex" @transitionX="transitionX"
				@animationfinish="animationfinish" :duration="50"></u-swiper>
		</view>
		<Round :countIndex="currentIndex" :list="list3" @click="roundClick" :dx="dx" :moveAllDx="390-30-30"></Round>
		<!-- #endif -->
	</view>
</template>

<script>
	import Round from "./round.vue"
	export default {

		components: {
			Round
		},
		data() {
			return {
				currentIndex: 0,
				list3: [
					'https://cdn.uviewui.com/uview/swiper/swiper3.png',
					'https://cdn.uviewui.com/uview/swiper/swiper2.png',
					'https://cdn.uviewui.com/uview/swiper/swiper1.png',
					'https://cdn.uviewui.com/uview/swiper/swiper3.png',
					'https://cdn.uviewui.com/uview/swiper/swiper1.png',
				],
				dx: 0
			}
		},
		methods: {
			itemClick(e) {
				console.log(e);
				this.currentIndex = e
			},
			roundClick(e) {
				console.log(e);
				this.currentIndex = e
			},
			transitionX(e) {
				console.log(e);
				this.dx = e
			},

			animationfinish(e) {
				console.log(e);
				this.currentIndex = e.current
			}

		}
	}
</script>

<style>

</style>
