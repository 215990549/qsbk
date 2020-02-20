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
		
		<view class="uni-textarea">
			<textarea placeholder="说一句话吧~" class="text"/>
		</view>
		
		<uploud-images @upload="upload"></uploud-images>
		
	</view>
</template>

<script>
	import uniNavBar from "../../components/uni-nav-bar/uni-nav-bar.vue"
	import uploudImages from "../../components/uploud-images.vue"
	export default {
		components:{
			uniNavBar,
			uploudImages
		},
		data() {
			return {
				// 隐私列表
				changeLook:['仅自己可见','所有人可见','仅好友可见'],
				// 隐私
				privacyIndex:1,
				imageList:[]
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
			},
			// 获取上传图片列表
			upload(v){
				this.imageList = v
				console.log(this.imageList.length)
			}
		}
	}
</script>

<style lang="scss" scoped>
.add-input{
	.text{
		height: 250rpx;
		width: auto;
		margin: 15rpx;
	}
	
}
</style>
