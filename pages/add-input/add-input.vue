<!-- 发布页 -->
<template>
	<view class="add-input">
		<!-- 顶部导航栏 -->
		<uni-nav-bar :statusBar = "true" 
			left-icon="back" @clickLeft="goBack" 
			rightText="发布" @clickRight="issue">
			<view class="f-jCenter-aCenter" style="width: 100%;" @tap="changePrivacy">
				{{privacy}}
				<view class="icon iconfont icon-xiala2"></view>
			</view>
		</uni-nav-bar> 
		<!-- 多行文本输入栏 -->
		<view class="uni-textarea">
			<textarea placeholder="说一句话吧~" class="text" v-model="text"/>
		</view>
		<!-- 上传多图组件 -->
		<uploud-images :imageList.sync = "imageList"></uploud-images>
		<!-- 弹出公告 -->
		<uni-popup type="center" ref="popup">
			<view class="notice">
				<view class="image">
					<image src="../../static/img/add-input/notice.png" mode="aspectFit" ></image>
				</view>
				<view class="">
					1、涉及黄色、政治、广告及骚扰信息
				</view>
				<view class="">
					2、涉及人身攻击
				</view>
				<view class="">
					3、留联系方式，透漏他人隐私
				</view>
				<view class="">
					一经核实将被封禁，情节严重者永久封禁
				</view>
				<button class="button" type="primary" @tap="$refs.popup.close()">
					朕知道了
				</button>
			</view>
		</uni-popup>
	</view>
</template>

<script>
	import uniNavBar from "../../components/uni-nav-bar/uni-nav-bar.vue"
	import uploudImages from "../../components/uploud-images.vue"
	import uniPopup from "../../components/uni-popup/uni-popup.vue"
	export default {
		components:{
			uniNavBar,
			uploudImages,
			uniPopup
		},
		data() {
			return {
				csfsj:0,
				// 隐私列表
				changeLook:['仅自己可见','所有人可见','仅好友可见'],
				// 隐私
				privacyIndex:1,
				imageList:[],
				// 是否保存草稿
				draftsFlag:false,
				text:""
			}
		},
		computed:{
			privacy:{
				get:function() {
					return (this.changeLook[this.privacyIndex])
				}
			}
		},
		onReady() {
			this.$refs.popup.open()
			uni.getStorage({
				key:"inputDrafts",
				success: (res) => {
					if(res != undefined && Object.keys(res).length != 0){
						this.imageList = res.data.imageList
						this.text = res.data.text
					}
				}
			}) 
			
		},
		// 监听返回上级页面
		onBackPress(options){
			if(this.draftsFlag){
				return false
			}else{
				this.saveDrafts()
				return true
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
			},
			// 判断是否要保存草稿
			saveDrafts(){
				uni.showModal({
					content:"是否保存当前编辑",
					cancelText:"不保存",
					confirmText:"保存",
					success: (v) => {
						// 点击保存
						if(v.confirm){
							uni.setStorage({
								key:"inputDrafts",
								data:{
									imageList:this.imageList,
									text:this.text
								}
							})
						}
					},
					complete: () => {
						this.goBack()
					}
				})
				this.draftsFlag = true
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
	.notice{
		background: #FEFEFE;
		height:550rpx;
		width: 550rpx;
		border-radius: 5px;
		padding: 30rpx;
		
		image{
			width: 550rpx;
			height: 200rpx;
			margin-bottom: 10rpx;
		}
		
		.button{
			background-color: #FFE934;
			color: black;
			margin-top: 30rpx;
		}
	}
}
</style>
