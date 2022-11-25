<template>
  <div>
      <div class="round" :style="setPosition" @click="itemClick"></div>
  </div>
</template>

<script>
    let timer = 0
    // import { raf,caf } from '../../utils/raf'
    export default {
        name: 'moveRound',
        props: {
            angle: { // 需要转动的角度
                type: Number,
                default: 0
            },
            bigR: { // 外层大圆半径
                type: Number,
                default: 0
            },
            minR: { //移动小圆半径
                type: Number,
                default: 0
            },
            backgroundColor: {
                type: String,
                default: '#7fffd4'
            },
			setAngle: { // 需要转动的角度
			    type: Number,
			    default: 0
			}
        },
        data() {
            return {
                top: '',
                right: '',
                // setAngle: this.angle
            }
        },
        mounted() {

        },
        computed: {
            /**
             * sin 对应 y 的值，转换为定位中距离顶部top等于 圆的半径 - y - 小圆半径（让圆心在圆弧上）
             * cos 对应 x 的值，转换为定位中距离右边right等于 圆的半径 - x - 小圆半径
             * **/ 
            setPosition( { top, right ,setAngle, bigR, minR, backgroundColor} ) {
                let size = minR*2 + 'px'

                let x = bigR * ( 1 - Math.cos(setAngle * Math.PI/180)) - minR
                let y = bigR * ( 1 - Math.sin(setAngle * Math.PI/180))  - minR

                right = x + 'px'
                top = y + 'px'
				// console.log(x,y);
                return {
                    top,
                    right,
                    width: size,
                    height: size,
                    backgroundColor
                }
            }
        },
        methods: {
			itemClick(){
				this.$emit('click')
			},
    //         toMove() {
    //         	// 调整 累加值，改变速度
    //             this.setAngle += 1
    //             // timer = raf(this.toMove)
				// timer = window.requestAnimationFrame(this.toMove)
    //             // 结束动画
    //             if(this.setAngle > this.angle) {
				// 	window.cancelAnimationFrame(timer)
    //                 // caf(timer)
    //                 // 也可以根据需要重复执行
    //                 // this.setAngle = 0
    //             }
    //         }
        }
    }
</script>

<style>
 .round{
    position: absolute;
    will-change: top,right;
    border-radius: 50%;
 }
</style>