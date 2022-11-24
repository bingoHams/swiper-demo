<template>
	<view>
		<swiper :options="swiperOption">
			<swiper-slide v-for="(item,index) in list3" :key="index">
				<div>12</div>
			</swiper-slide>
		</swiper>
	</view>
</template>

<script>
	import {
		swiper,
		swiperSlide
	} from 'vue-awesome-swiper';
	import 'swiper/dist/css/swiper.css'

	export default {
		components: {
			// 注册组件
			swiper,
			swiperSlide
		},

		data() {
			return {
				swiperOption: {
					notNextTick: false,
					pagination: {
						el: '.swiper-pagination'
					},
					loop: true,
					touchRatio: 2, // 触摸滑动的顺畅度
					initialSlide: 1, // 默认展示页
					autoplay: true, // 是否自动播放
					speed: 500, // 播放速度
					slidesPerView: 'auto',
					centeredSlides: true,
					paginationClickable: true,
					spaceBetween: 5, // 模块之间的间隔
					on: {
						slideChangeTransitionEnd: function() {
							// 处理手动操作轮播图后后不再自动轮播
							this.autoplay.start();
						}
					}
				},
				list3: [
					'https://cdn.uviewui.com/uview/swiper/swiper3.png',
					'https://cdn.uviewui.com/uview/swiper/swiper2.png',
					'https://cdn.uviewui.com/uview/swiper/swiper1.png',
					'https://cdn.uviewui.com/uview/swiper/swiper3.png',
					'https://cdn.uviewui.com/uview/swiper/swiper1.png',
				]

			}
		},
		methods: {

		}
	}
</script>

<style>

</style>
