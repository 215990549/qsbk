<!-- 发布页 -->
<template>
	<view class="add-input">
		<uni-nav-bar :statusBar = "true" 
			left-icon="back" @clickLeft="goBack" 
			rightText="发布" @clickRight="issue">
			<view class="f-jCenter-aCenter" style="width: 100%;" @tap="changePrivacy">
				{{privacy}}
				<view class="icon iconfont icon-xiala2"></view>
			</view>
		</uni-nav-bar> 
	</view>
</template>

<script>
	import uniNavBar from "../../components/uni-nav-bar/uni-nav-bar.vue"
	export default {
		components:{
			uniNavBar
		},
		data() {
			return {
				// 隐私列表
				changeLook:['仅自己可见','所有人可见','仅好友可见'],
				// 隐私
				privacyIndex:1
			}
		},
		computed:{
			privacy:{
				get:function() {
					return (this.changeLook[this.privacyIndex])
				}
			}
		},
		methods: {
			// 返回按钮
			goBack(){
				uni.navigateBack({
					delta:1
				})
			},
			// 发布
			issue(){
				console.log("发布")
			},
			// 更改隐私设置
			changePrivacy(){
				uni.showActionSheet({
					itemList:this.changeLook,
					success: (res) => {
						this.privacyIndex = res.tapIndex
					}
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
.add-input{
	
	
}
</style>
