<template>
	<div style="display: flex;">
		<div class="father">
			<div class="arc_bo">
				<move-round v-for="(item,index) in list" :minR="15" :bigR="400" :setAngle="item.angle" ref="mRound1"
					@click="itemClick(index)">
				</move-round>
				<!-- <move-round :minR="15" :bigR="250" :setAngle="angle3" ref="mRound1"> </move-round> -->
			</div>
		</div>
		<view class="u-demo-block">
			<u-swiper :list="list3" :previousMargin="previousMargin" :circular="false" :nextMargin="nextMargin"
				:autoplay="false" radius="5" bgColor="#ffffff" @click="itemClick" :current="currentIndex"
				@transitionX="transitionX" :duration="50">
			</u-swiper>
		</view>
		<!-- <span class="start" @click="toMove">开始</span> -->
	</div>
</template>

<script>
	import {
		forIn
	} from 'lodash'
	import moveRound from './moveRound.vue'
	export default {
		name: 'arcMoveAni',
		components: {
			moveRound
		},
		created() {
			var angle = 100
			var angle1 = 10
			for (var i = 0; i < 5; i++) {
				angle -= angle1
				this.list.push({
					"angle": angle
				})
				this.oldList.push({
					"angle": angle
				})
			}
		},
		data() {
			return {
				list: [],
				oldList: [],
				moveAngle: 0,
				currentIndex: 0,
				list3: [
					'https://cdn.uviewui.com/uview/swiper/swiper3.png',
					'https://cdn.uviewui.com/uview/swiper/swiper2.png',
					'https://cdn.uviewui.com/uview/swiper/swiper1.png',
					'https://cdn.uviewui.com/uview/swiper/swiper3.png',
					'https://cdn.uviewui.com/uview/swiper/swiper1.png',
				],
				intervalAngle: 10,
				previousMargin: 30,
				nextMargin: 30

			}
		},
		computed: {
			swiperDistance() {
				return 390 - this.previousMargin - this.nextMargin
			}
		},
		methods: {
			transitionX(e) {
				var add = (e > 0 ? 1 : -1)
				var moveAngle = (e / this.swiperDistance) * this.intervalAngle
				this.list.forEach((item, index) => {
					item.angle = this.oldList[index].angle + moveAngle
				})
				if (Math.abs(moveAngle) == this.intervalAngle) {
					this.oldList.forEach(item => {
						item.angle += this.intervalAngle * add
					})
				}

			},
			itemClick(e) {
				this.currentIndex = e
			}

		}
	}
</script>

<style scoped>
	.father {
		position: absolute;
		left: calc(50% - 400px);
		height: 200px;
		overflow: hidden;
		background-color: rebeccapurple;

	}

	.arc_bo {
		/* margin: 0 auto; */
		width: 800px;
		height: 800px;
		border-radius: 50%;
		border: 5px solid #ff0000;
		position: relative;
		margin-top: 25px;
	}

	.start {
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
		color: #f40;
		width: 1rem;
		height: 1rem;
		border-radius: 50%;
		border: 1px solid #ccc;
		text-align: center;
		/* line-height: 1rem; */
	}

	.u-demo-block {
		margin-top: 250px;
	}
</style>
