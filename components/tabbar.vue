<!-- 横向滚动顶部导航栏组件 -->
<template>
	<view class="uni-tab-bar">
		<scroll-view scroll-x="true" class="uni-swiper-tab">
			<block v-for="(item, index) in list" :key="item.id">
				<view class="swiper-tab-list" :class="{ active: active == index }" @tap="tabTap(index)">
					{{ item.name }}
					<view class="list-flag"></view>
				</view>
			</block>
		</scroll-view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			
		};
	},
	props: {
		list: Array,
		active: Number
	},
	methods: {
		tabTap(index) {
			this.active = index;
			let e = {
				detail:{
					current:index
				}
			}
			this.$emit("swiperChange",e)
		}
	}
};
</script>

<style lang="scss" scoped>
.uni-swiper-tab {
	border-bottom: none;
}
.active {
	color: #343434;

	.list-flag {
		width: 60rpx;
		border: 6rpx solid #fede33;
		border-radius: 6rpx;
		margin: -12rpx auto 0;
	}
}
</style>
