<template>
	<view class="bigBox">
		<view class="content">
			<view class="bubbleBox">
				<view class="bubbleItem" @click="finishedItem(item)" v-for="item in bubbleList" :key="item.id"
					:style="{'width': item.widthSize + 'rpx','height': item.widthSize + 'rpx','animation': 'square' + item.id + ' ' + item.speed + 's' + ' ' + 'infinite','top': item.top + 'rpx','left': item.left + 'rpx'}">
					{{item.name}}
				</view>
			</view>
		</view>
		<view class="shadeBox" v-if="showShadeBox" @click="closeShadeBox">
			<view>{{checkedMsg.name}}</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				showShadeBox: false,
				checkedMsg: {},
				coordinatesList: [
					[100, 100],
					[500, 150],
					[251, 251],
					[450, 350],
					[100, 400],
					[300, 90],
					[270, 430],
					[120, 600],
					[500, 500],
					[320, 660]
				],
				bubbleList: [{
						id: '1',
						name: '喝八杯水',
						widthSize: null,
						speed: null,
						left: null,
						top: null
					},
					{
						id: '2',
						name: '不吃外卖',
						widthSize: null,
						speed: null,
						left: null,
						top: null
					},
					{
						id: '3',
						name: '不久坐',
						widthSize: null,
						speed: null,
						left: null,
						top: null
					},
					{
						id: '4',
						name: '步行超过一千米',
						widthSize: null,
						speed: null,
						left: null,
						top: null
					},
					{
						id: '5',
						name: '23点之前睡觉',
						widthSize: null,
						speed: null,
						left: null,
						top: null
					}
				]
			}
		},
		onLoad() {

		},
		methods: {
			// 初始化
			getBubbleList() {
				this.bubbleList.forEach(item => {
					item.widthSize = Math.floor(Math.random() * (20)) + 80
					item.speed = Math.floor(Math.random() * (4)) + 8
					const randomIndex = Math.floor(Math.random() * this.coordinatesList.length + 1) - 1
					item.left = this.coordinatesList[randomIndex][0]
					item.top = this.coordinatesList[randomIndex][1]
					this.coordinatesList.splice(randomIndex,1)
				})
			},
			// 点击事件
			finishedItem(item) {
				this.checkedMsg = item
				this.showShadeBox = true
				const index = this.bubbleList.findIndex(ev => item.id === ev.id)
				this.bubbleList.splice(index, 1)
			},
			//关闭弹框
			closeShadeBox() {
				this.showShadeBox = false
			}
		},
		created() {
			this.$nextTick(() => {
				this.getBubbleList()
			})
		}
	}
</script>

<style>
	.bigBox {
		width: 100%;
		height: 100vh;
		overflow: hidden;
		position: relative;
	}

	.content {
		width: 100%;
		height: 100vh;
	}

	.bubbleBox {
		width: 100%;
		height: 100rpx;
		padding: 20rpx;
		position: relative;
	}

	.bubbleItem {
		border-radius: 50%;
		background: palegreen;
		display: flex;
		justify-content: center;
		align-items: center;
		text-align: center;
		color: cadetblue;
		font-size: 24rpx;
		padding: 20rpx;
		animation-direction: alternate;
		animation-timing-function: ease-in-out;
		position: absolute;
	}

	@keyframes square1 {
		0% {
			transform: scale(1)
		}

		25% {
			transform: scale(1.2)
		}

		50% {
			transform: scale(1)
		}

		75% {
			transform: scale(1.2)
		}

		100% {
			transform: scale(1)
		}
	}

	@keyframes square2 {
		0% {
			transform: scale(1)
		}

		25% {
			transform: scale(0.9)
		}

		50% {
			transform: scale(1)
		}

		75% {
			transform: scale(0.9)
		}

		100% {
			transform: scale(1)
		}
	}

	@keyframes square3 {
		0% {
			transform: scale(1)
		}

		25% {
			transform: scale(1.1)
		}

		50% {
			transform: scale(1)
		}

		75% {
			transform: scale(1.1)
		}

		100% {
			transform: scale(1)
		}
	}

	@keyframes square4 {
		0% {
			transform: scale(1)
		}

		25% {
			transform: scale(1.2)
		}

		50% {
			transform: scale(1)
		}

		75% {
			transform: scale(1.2)
		}

		100% {
			transform: scale(1)
		}
	}

	,
	@keyframes square5 {
		0% {
			transform: scale(1)
		}

		25% {
			transform: scale(0.8)
		}

		50% {
			transform: scale(1)
		}

		75% {
			transform: scale(0.8)
		}

		100% {
			transform: scale(1)
		}
	}

	.shadeBox {
		width: 100%;
		height: 100vh;
		background: rgba(0, 0, 0, .6);
		position: absolute;
		top: 0;
		left: 0;
		color: white;
		font-size: 52rpx;
		display: flex;
		justify-content: center;
		align-items: center;
	}
</style>
