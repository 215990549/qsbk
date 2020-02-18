<!-- 上拉加载组件 -->
<template>
	<view>
		<view class="loed-text">{{loadText}}</view>
	</view>
</template>

<script>
	export default {
		props:{
			loadText:String
		}
	}
</script>

<style lang="scss" scoped>
	.loed-text{
		padding: 15rpx;
		text-align: center;
		color: #d5d5d5;
	}
</style>
