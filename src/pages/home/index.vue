<template>
	<view class="home-content">
		<image class="logo" src="/static/bagua.jpg"></image>
		<view>
			<gua-item :guaArr.sync="guaData"></gua-item>
		</view>
		<view class="intor" v-if="currentGua">
			<view class="big-text">{{currentGua.guaName}}</view>
			<view>:</view>
			<view class="small-text">{{currentGua.guaDetail}}</view>
		</view>
		<view class="go-detail">详情>></view>
	</view>
</template>

<script>
import guaItem from '@/components/gua.vue'
	export default {
		components: { guaItem },
		data() {
			return {
				guaData: [],
				firstGua: {},
				allGua: [] // 所有的挂
			}
		},
		computed: {
			currentGua() {
				if (this.guaData.length) {
					const guaStr = this.guaData.join('')
					const currentGua = this.allGua.find(item => {
						return item.guaXiang === guaStr + ''
					})
					return currentGua || {}
				}
				
			}
		},
		onLoad() {
			this.allGua = getApp().globalData.guaList.gua || [];
			const firstGua = this.allGua[0] || {}
			console.log('firstGua', firstGua)
			this.firstGua = firstGua
			const guaXiang = firstGua.guaXiang
			for(let i = 0; i < guaXiang.length; i++) {
				this.guaData.push(+guaXiang[i])
			}
		},
		methods: {

		}
	}
</script>

<style lang="scss">
/* @import '@/styles/util.scss'; */
.home-content {
	width: 750rpx;
	min-height: calc(100vh - 10px);
	// background-color:aqua;
	display: flex;
	flex-direction: column;
	align-items: center;
	justify-content: center;
	.logo {
		width: 350rpx;
		height: 350rpx;
		margin-bottom: 10px;
	}
	.intor {
		width: 750rpx;
		padding: 10px 10px;
		display: flex;
		align-items: center;
		color: $uni-text-color;
		font-size: 40rpx;
		.big-text {
			font-size: 100rpx;
			color: $uni-color-paragraph;
			margin-right: 20rpx;
			margin-left: 20rpx;
		}
		.small-text {
			margin-left: 20rpx;
		}
	}
	.go-detail {
		color: $uni-color-paragraph;
	}
}
</style>
