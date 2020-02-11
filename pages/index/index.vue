<template>
	<view class="content">
		<image class="logo" src="/static/logo.png"></image>
		<view class="text-area">
			<text class="title">{{title}}</text>
		</view>
		<span>矢量图片测试</span> 
		<button type="primary"@click='animate'>动画测试</button>
		<view class="icon iconfont icon-pic animated bounceIn" v-show="animateFlag"></view>
		
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello',
				animateFlag:false
			}
		},
		onLoad() {

		},
		methods: {
			animate () {
				this.animateFlag = !this.animateFlag
				
			}
		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
	
	.icon-pic{
		font-size: 120rpx;
	}
</style>
