<template>
	<div style="height: 200px; overflow: hidden; border: 1px solid yellow;margin: 0 auto;text-align: center; ">
		<div id="div1">
			<div v-for="(item,index) in list" @click="roundIndex(index)" class="item"
				:style="{'transform':'rotate(' + ((index*angle)+initAngle) + 'deg)'}"
				:class="{choosed:index===countIndex}">
				{{index}}
			</div>
			<!-- <div id="div3">
				3
			</div>
			<div id="div4">
				4
			</div>
			<div id="div5">5</div>
			<div id="div6">6</div>
			<div id="div7">7</div> -->
		</div>
	</div>
</template>

<script>
	export default {
		props: {
			countIndex: {
				type: Number,
				default: 0
			},
			list: {
				type: Array,
				default: []
			},
			dx: {
				type: Number,
				default: 0
			},
			angle: {
				type: Number,
				default: 15

			},
			initAngle: {
				type: Number,
				default: 0
			},
			moveAllDx: {
				type: Number,
				default: 390
			},

		},
		watch: {
			countIndex(val, preVal) {
				// var dif = (preVal - val) * this.angle
				// this.curDeg = this.curDeg + dif
			},
			dx(val, preVal) {
				const circle = document.getElementById('div1')
				// console.log(this.angle * (val / this.moveAllDx));
				var moveAngle = this.angle * (val / this.moveAllDx) * -1

				// console.log(this.curDeg, this.curDeg + moveAngle);
				// this.curDeg = moveAngle
				circle.style.transform = 'rotate(' + (this.curDeg + moveAngle) + 'deg)'
				if (Math.abs(moveAngle) % this.angle == 0) {
					this.curDeg += moveAngle
				}
			},
			curDeg(val) {
				console.log(val);
				// const circle = document.getElementById('div1')
				// circle.style.transform = 'rotate(' + val + 'deg)'
			}
		},
		computed: {

		},
		data() {
			return {
				curDeg: this.initAngle,
			}
		},

		methods: {
			roundIndex(e) {
				this.$emit('click', e)
			}
		}
	}
</script>

<style>
	#div1 {
		position: relative;
		height: 500px;
		width: 500px;
		/* border: 1px solid black; */
		border: 4px solid rgba(123, 228, 252, 1);
		border-radius: 50%;
		transition: transform 1s;
		/* transform: translateX(-50px) */
		margin-top: 20px;
	}

	.item {
		width: 50px;
		height: 30px;
		position: absolute;
		top: -18px;
		left: calc(50% - 25px);
		border: 1px solid black;
		background-color: red;
		/* transform: rotate(0deg); */

		transform-origin: 25px 268px;
	}

	.choosed {
		background-color: yellow;
	}


	#div2 {
		width: 50px;
		height: 30px;
		position: absolute;
		/* top:-15px; */
		left: calc(50% - 25px);
		border: 1px solid black;
		background-color: red;
		transform: rotate(0deg);
		transform-origin: 25px 250px;
	}


	#div3 {
		width: 50px;
		height: 30px;
		position: absolute;
		//top:15px;
		left: calc(50% - 25px);
		border: 1px solid black;
		background-color: red;
		transform: rotate(45deg);
		transform-origin: 25px 250px;
	}

	#div4 {
		width: 50px;
		height: 30px;
		position: absolute;
		border: 1px solid black;
		background-color: red;
		//top:15px;
		left: calc(50% - 25px);
		transform: rotate(90deg);
		transform-origin: 25px 250px;
	}

	#div5 {
		width: 50px;
		height: 30px;
		position: absolute;
		//top:15px;
		left: calc(50% - 25px);
		border: 1px solid black;
		background-color: red;
		transform: rotate(135deg);
		transform-origin: 25px 250px;
	}

	#div6 {
		width: 50px;
		height: 30px;
		position: absolute;
		//top:15px;
		left: calc(50% - 25px);
		border: 1px solid black;
		background-color: red;
		transform: rotate(180deg);
		transform-origin: 25px 250px;
	}

	#div7 {
		width: 50px;
		height: 30px;
		position: absolute;
		//top:15px;
		left: calc(50% - 25px);
		border: 1px solid black;
		background-color: red;
		transform: rotate(225deg);
		transform-origin: 25px 250px;
	}
</style>
