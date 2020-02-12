<template>
	<view class="index">
		
		<view class="card">
			
			<!-- 用户信息 -->
			<view class="message f-jBetween f-aCenter">
				<view class="user f-jBetween f-aCenter">
					<image 
						src="https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1581537044717&di=1d4528e3684f1eacbc0e4481d0bf20ef&imgtype=0&src=http%3A%2F%2Fbbs.cnlinfo.net%2Fup%2Ftou%2F150611164743.jpg" 
							mode="aspectFit" 
							lazy-load></image>
					<p>用户名</p>
				</view>
				<view class="concern f-jBetween f-aCenter">
					<span class = "icon iconfont icon-jia"></span>
					<p>关注</p>
				</view>
			</view>
			
			<!-- 内容 -->
			<view class="content">
				<h2>我是标题</h2>
				<image 
					src="https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=3313838802,2768404782&fm=26&gp=0.jpg" 
					mode="widthFix" 
					lazy-load></image>
			</view>
			
			<!-- 计数 -->
			<view class="count f-jBetween">
				<view class="attitude f-jBetween">
					<view class="like f-jBetween f-aCenter">
						<span class="icon iconfont icon-xiao"></span>
						<p>999</p>
					</view>
					<view class="disgust f-jBetween f-aCenter">
						<span class="icon iconfont icon-ku"></span>
						<p>999</p>
					</view>
				</view>
				<view class="active f-jBetween">
					<view class="comment f-jBetween f-aCenter">
						<span class="icon iconfont icon-pinglun"></span>
						<p>999</p>
					</view>
					<view class="transmit f-jBetween f-aCenter">
						<span class="icon iconfont icon-zhuanfa"></span>
						<p>999</p>
					</view>
				</view>
			</view>
		</view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		onLoad() {

		}
	}
</script>

<style lang="scss">
	.f-jBetween{
		// 主轴方向两边对齐
		display: flex;
		justify-content: space-between;
	}
	.f-aCenter{
		// 侧轴方向居中对齐
		display: flex;
		align-items:center;
	}
	.f{
		// 开启flex
		display: flex;
	}
	.index{
		.card{
			padding: 20rpx;
			.message{
				.user{
					image{
						width: 80rpx;
						height: 80rpx;
						border-radius: 50%;
					}
				}
			}
		}
	}
</style>
