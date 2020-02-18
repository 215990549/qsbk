<!-- 信息卡片组件 -->
<template>
	<view class="card animated flipInY" >
		<!-- 用户信息 -->
		<view class="message f-jBetween f-aCenter ">
			<view class="user f-jBetween f-aCenter">
				<image :src="item.lconUrl" mode="aspectFit" lazy-load></image>
				{{ item.userName }}
			</view>
			<view 
				class="concern f-jBetween f-aCenter" 
				:class="{concernFlag:!item.concernFlag}"
				@tap="tapConcern">
				<view class="icon iconfont icon-jia" v-show="!item.concernFlag"></view>
				<view>{{item.concernFlag ? '取消关注' : '关注'}}</view>
			</view>
		</view>

		<!-- 内容 -->
		<view class="content">
			<view class="title">{{ item.content.title }}</view>
			<template v-if="item.content.type == 'img'">
				<!-- 图片 -->
				<view class="f-jCenter-aCenter"><image :src="item.content.imgUrl" mode="widthFix" lazy-load></image></view>
			</template>
			<template v-else>
				<!-- 视频 -->
				<view class="f-jCenter-aCenter">
					<image :src="item.content.video.previewUrl" mode="widthFix" lazy-load></image>
					<view class="icon iconfont icon-bofang f-jCenter-aCenter"></view>
					<view class="count">{{ item.content.video.viewCounts }}次 播放 {{ item.content.video.duration }}</view>
				</view>
			</template>
		</view>

		<!-- 计数 -->
		<view class="count f-jBetween">
			<view class="attitude f-jBetween">
				<view 
					class="like f-jBetween f-aCenter" 
					:class="{flag:item.attitude.attitudeFlag == 1}"
					@tap="tapAttitude('like')">
					<span class="icon iconfont icon-xiao"></span>
					<view class="num">{{ item.attitude.likeNum }}</view>
				</view>
				<view 
					class="disgust f-jBetween f-aCenter" 
					:class="{flag:item.attitude.attitudeFlag == 2}"
					@tap="tapAttitude('disgust')">
					<span class="icon iconfont icon-ku"></span>
					<view class="num">{{ item.attitude.disgustNum }}</view>
				</view>
			</view>
			<view class="active f-jBetween">
				<view class="comment f-jBetween f-aCenter">
					<span class="icon iconfont icon-pinglun"></span>
					<view class="num">{{ item.commentNum }}</view>
				</view>
				<view class="transmit f-jBetween f-aCenter">
					<span class="icon iconfont icon-zhuanfa"></span>
					<view class="num">{{ item.transmitNum }}</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			
		};
	},
	onLoad() {},
	props:{
		item:Object,
		index:Number,
		index1:Number
	},
	methods:{
		// 更改关注状态
		tapConcern(){
			console.log(this.item.concernFlag)
			this.$emit("tapConcern",this.index,this.index1)
			if(!this.item.concernFlag){
				uni.showToast({
					title:"取消成功"
				})
			}else{
				uni.showToast({
					title:"关注成功"
				})
			}
		},
		// 顶/踩功能
		tapAttitude(v){
			let attitude = {
				index:this.index,
				index1:this.index1,
				attitudeFlag:v == "like" ? 1 : 2
			}
			this.$emit("tapAttitude",attitude)
		}
	}
};
</script>

<style lang="scss" scoped>
	.card {
		padding: 20rpx;
		border-bottom: 1rpx solid #f1f1f1;
		.message {
			.user {
				color: #989898;
				font-size: 30rpx;

				image {
					width: 90rpx;
					height: 90rpx;
					border-radius: 50%;
					margin-right: 20rpx;
				}
			}
			.concern {
				background-color: #f4f4f4;
				padding: 0 10rpx;
				border-radius: 10rpx;
				.icon-jia {
					margin-right: 5rpx;
				}
				view{
					font-size: 26rpx;
				}
			}
			.concernFlag{
				background-color: #F5DEB3;
			}
		}

		.content {
			margin: 20rpx 0;
			position: relative;
			.title {
				font-size: 36rpx;
				margin-bottom: 5rpx;
			}
			image {
				border-radius: 15rpx;
				width: 100%;
			}
			.icon-bofang {
				font-size: 150rpx;
				position: absolute;
				color: #ffffff;
			}
			.count {
				position: absolute;
				bottom: 10rpx;
				right: 10rpx;
				color: #ffffff;
				background-color: rgba(51, 51, 51, 0.72);
				font-size: 26rpx;
				padding: 0 16rpx;
				border-radius: 26rpx;
			}
		}

		.count {
			color: #d5d5d5;
			.num {
				margin: 0 10rpx;
			}
			.active{
				color: #d5d5d5;
			}
			.flag{
				color: #FF7F24;
			}
		}
	}
</style>
