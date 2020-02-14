<template>
	<view class="index">
		
		<tab-bar :list="tabBarList" :active="current" @swiperChange="swiperChange"></tab-bar>

		<view class="uni-tab-bar" >
			<swiper 
				class="swiper-box" 
				:style = "{height: tabHeight + 'px'}" 
				@change="swiperChange"
				:current="current">
				<swiper-item v-for="(list, index) in lists" :key="index" >
					<scroll-view scroll-y class="list">
						<block v-for="(item, index1) in list" :key="index1">
							<card :item="item"></card>
						</block>
					</scroll-view>
				</swiper-item>
			</swiper>
		</view>
		
	</view>
</template>

<script>
import card from '../../components/card.vue';
import tabBar from '../../components/tabbar.vue';
export default {
	components: {
		card,
		tabBar
	},
	data() {
		return {
			// 信息数据
			lists: [
				[
					{
						lconUrl: 'http://pic1.zhimg.com/50/v2-af12f7b6f7eb2f2f5f7e2f3b7880cf01_hd.jpg', // 头像地址
						userName: '关注', // 用户名
						concernFlag: false, // 是否关注
						content: {
							title: '动次打次抖抖抖', // 内容标题
							type: 'video', // 内容类型，img代表图片，video代表视频
							imgUrl: '', // 图片地址
							video: {
								previewUrl: 'http://img2.imgtn.bdimg.com/it/u=2973939870,266577806&fm=26&gp=0.jpg', // 预览图片地址
								viewCounts: '17854 ', // 播放量
								duration: '2:18' // 视频时长
							}
						},
						attitude: {
							attitudeFlag: 0, // 0表示未发表喜恶，1表示喜欢，2表示厌恶
							likeNum: 72, // 喜欢数量
							disgustNum: 3 // 厌恶数量
						},
						commentNum: 166, // 评论数量
						transmitNum: 56 // 转发数量
					},
					{
						lconUrl:
							'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1581537044717&di=1d4528e3684f1eacbc0e4481d0bf20ef&imgtype=0&src=http%3A%2F%2Fbbs.cnlinfo.net%2Fup%2Ftou%2F150611164743.jpg', // 头像地址
						userName: '小飞飞', // 用户名
						concernFlag: false, // 是否关注
						content: {
							title: '飞飞风景好，耶耶耶', // 内容标题
							type: 'img', // 内容类型，img代表图片，video代表视频
							imgUrl: 'https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=3313838802,2768404782&fm=26&gp=0.jpg', // 图片地址
							video: {
								previewUrl: '', // 预览图片地址
								viewCounts: '20w', // 播放量
								duration: '2:18' // 视频时长
							}
						},
						attitude: {
							attitudeFlag: 0, // 0表示未发表喜恶，1表示喜欢，2表示厌恶
							likeNum: 16, // 喜欢数量
							disgustNum: 1 // 厌恶数量
						},
						commentNum: 54, // 评论数量
						transmitNum: 13 // 转发数量
					}
				],
				[
					{
						lconUrl: 'http://pic1.zhimg.com/50/v2-af12f7b6f7eb2f2f5f7e2f3b7880cf01_hd.jpg', // 头像地址
						userName: '推荐', // 用户名
						concernFlag: false, // 是否关注
						content: {
							title: '动次打次抖抖抖', // 内容标题
							type: 'video', // 内容类型，img代表图片，video代表视频
							imgUrl: '', // 图片地址
							video: {
								previewUrl: 'http://img2.imgtn.bdimg.com/it/u=2973939870,266577806&fm=26&gp=0.jpg', // 预览图片地址
								viewCounts: '17854 ', // 播放量
								duration: '2:18' // 视频时长
							}
						},
						attitude: {
							attitudeFlag: 0, // 0表示未发表喜恶，1表示喜欢，2表示厌恶
							likeNum: 72, // 喜欢数量
							disgustNum: 3 // 厌恶数量
						},
						commentNum: 166, // 评论数量
						transmitNum: 56 // 转发数量
					},
					{
						lconUrl:
							'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1581537044717&di=1d4528e3684f1eacbc0e4481d0bf20ef&imgtype=0&src=http%3A%2F%2Fbbs.cnlinfo.net%2Fup%2Ftou%2F150611164743.jpg', // 头像地址
						userName: '小飞飞', // 用户名
						concernFlag: false, // 是否关注
						content: {
							title: '飞飞风景好，耶耶耶', // 内容标题
							type: 'img', // 内容类型，img代表图片，video代表视频
							imgUrl: 'https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=3313838802,2768404782&fm=26&gp=0.jpg', // 图片地址
							video: {
								previewUrl: '', // 预览图片地址
								viewCounts: '20w', // 播放量
								duration: '2:18' // 视频时长
							}
						},
						attitude: {
							attitudeFlag: 0, // 0表示未发表喜恶，1表示喜欢，2表示厌恶
							likeNum: 16, // 喜欢数量
							disgustNum: 1 // 厌恶数量
						},
						commentNum: 54, // 评论数量
						transmitNum: 13 // 转发数量
					}
				],
				[
					{
						lconUrl: 'http://pic1.zhimg.com/50/v2-af12f7b6f7eb2f2f5f7e2f3b7880cf01_hd.jpg', // 头像地址
						userName: '体育', // 用户名
						concernFlag: false, // 是否关注
						content: {
							title: '动次打次抖抖抖', // 内容标题
							type: 'video', // 内容类型，img代表图片，video代表视频
							imgUrl: '', // 图片地址
							video: {
								previewUrl: 'http://img2.imgtn.bdimg.com/it/u=2973939870,266577806&fm=26&gp=0.jpg', // 预览图片地址
								viewCounts: '17854 ', // 播放量
								duration: '2:18' // 视频时长
							}
						},
						attitude: {
							attitudeFlag: 0, // 0表示未发表喜恶，1表示喜欢，2表示厌恶
							likeNum: 72, // 喜欢数量
							disgustNum: 3 // 厌恶数量
						},
						commentNum: 166, // 评论数量
						transmitNum: 56 // 转发数量
					},
					{
						lconUrl:
							'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1581537044717&di=1d4528e3684f1eacbc0e4481d0bf20ef&imgtype=0&src=http%3A%2F%2Fbbs.cnlinfo.net%2Fup%2Ftou%2F150611164743.jpg', // 头像地址
						userName: '小飞飞', // 用户名
						concernFlag: false, // 是否关注
						content: {
							title: '飞飞风景好，耶耶耶', // 内容标题
							type: 'img', // 内容类型，img代表图片，video代表视频
							imgUrl: 'https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=3313838802,2768404782&fm=26&gp=0.jpg', // 图片地址
							video: {
								previewUrl: '', // 预览图片地址
								viewCounts: '20w', // 播放量
								duration: '2:18' // 视频时长
							}
						},
						attitude: {
							attitudeFlag: 0, // 0表示未发表喜恶，1表示喜欢，2表示厌恶
							likeNum: 16, // 喜欢数量
							disgustNum: 1 // 厌恶数量
						},
						commentNum: 54, // 评论数量
						transmitNum: 13 // 转发数量
					}
				],
				[
					{
						lconUrl: 'http://pic1.zhimg.com/50/v2-af12f7b6f7eb2f2f5f7e2f3b7880cf01_hd.jpg', // 头像地址
						userName: '热点', // 用户名
						concernFlag: false, // 是否关注
						content: {
							title: '动次打次抖抖抖', // 内容标题
							type: 'video', // 内容类型，img代表图片，video代表视频
							imgUrl: '', // 图片地址
							video: {
								previewUrl: 'http://img2.imgtn.bdimg.com/it/u=2973939870,266577806&fm=26&gp=0.jpg', // 预览图片地址
								viewCounts: '17854 ', // 播放量
								duration: '2:18' // 视频时长
							}
						},
						attitude: {
							attitudeFlag: 0, // 0表示未发表喜恶，1表示喜欢，2表示厌恶
							likeNum: 72, // 喜欢数量
							disgustNum: 3 // 厌恶数量
						},
						commentNum: 166, // 评论数量
						transmitNum: 56 // 转发数量
					},
					{
						lconUrl:
							'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1581537044717&di=1d4528e3684f1eacbc0e4481d0bf20ef&imgtype=0&src=http%3A%2F%2Fbbs.cnlinfo.net%2Fup%2Ftou%2F150611164743.jpg', // 头像地址
						userName: '小飞飞', // 用户名
						concernFlag: false, // 是否关注
						content: {
							title: '飞飞风景好，耶耶耶', // 内容标题
							type: 'img', // 内容类型，img代表图片，video代表视频
							imgUrl: 'https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=3313838802,2768404782&fm=26&gp=0.jpg', // 图片地址
							video: {
								previewUrl: '', // 预览图片地址
								viewCounts: '20w', // 播放量
								duration: '2:18' // 视频时长
							}
						},
						attitude: {
							attitudeFlag: 0, // 0表示未发表喜恶，1表示喜欢，2表示厌恶
							likeNum: 16, // 喜欢数量
							disgustNum: 1 // 厌恶数量
						},
						commentNum: 54, // 评论数量
						transmitNum: 13 // 转发数量
					}
				],
				[
					{
						lconUrl: 'http://pic1.zhimg.com/50/v2-af12f7b6f7eb2f2f5f7e2f3b7880cf01_hd.jpg', // 头像地址
						userName: '财经', // 用户名
						concernFlag: false, // 是否关注
						content: {
							title: '动次打次抖抖抖', // 内容标题
							type: 'video', // 内容类型，img代表图片，video代表视频
							imgUrl: '', // 图片地址
							video: {
								previewUrl: 'http://img2.imgtn.bdimg.com/it/u=2973939870,266577806&fm=26&gp=0.jpg', // 预览图片地址
								viewCounts: '17854 ', // 播放量
								duration: '2:18' // 视频时长
							}
						},
						attitude: {
							attitudeFlag: 0, // 0表示未发表喜恶，1表示喜欢，2表示厌恶
							likeNum: 72, // 喜欢数量
							disgustNum: 3 // 厌恶数量
						},
						commentNum: 166, // 评论数量
						transmitNum: 56 // 转发数量
					},
					{
						lconUrl:
							'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1581537044717&di=1d4528e3684f1eacbc0e4481d0bf20ef&imgtype=0&src=http%3A%2F%2Fbbs.cnlinfo.net%2Fup%2Ftou%2F150611164743.jpg', // 头像地址
						userName: '小飞飞', // 用户名
						concernFlag: false, // 是否关注
						content: {
							title: '飞飞风景好，耶耶耶', // 内容标题
							type: 'img', // 内容类型，img代表图片，video代表视频
							imgUrl: 'https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=3313838802,2768404782&fm=26&gp=0.jpg', // 图片地址
							video: {
								previewUrl: '', // 预览图片地址
								viewCounts: '20w', // 播放量
								duration: '2:18' // 视频时长
							}
						},
						attitude: {
							attitudeFlag: 0, // 0表示未发表喜恶，1表示喜欢，2表示厌恶
							likeNum: 16, // 喜欢数量
							disgustNum: 1 // 厌恶数量
						},
						commentNum: 54, // 评论数量
						transmitNum: 13 // 转发数量
					}
				],
				[
					{
						lconUrl: 'http://pic1.zhimg.com/50/v2-af12f7b6f7eb2f2f5f7e2f3b7880cf01_hd.jpg', // 头像地址
						userName: '娱乐', // 用户名
						concernFlag: false, // 是否关注
						content: {
							title: '动次打次抖抖抖', // 内容标题
							type: 'video', // 内容类型，img代表图片，video代表视频
							imgUrl: '', // 图片地址
							video: {
								previewUrl: 'http://img2.imgtn.bdimg.com/it/u=2973939870,266577806&fm=26&gp=0.jpg', // 预览图片地址
								viewCounts: '17854 ', // 播放量
								duration: '2:18' // 视频时长
							}
						},
						attitude: {
							attitudeFlag: 0, // 0表示未发表喜恶，1表示喜欢，2表示厌恶
							likeNum: 72, // 喜欢数量
							disgustNum: 3 // 厌恶数量
						},
						commentNum: 166, // 评论数量
						transmitNum: 56 // 转发数量
					},
					{
						lconUrl:
							'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1581537044717&di=1d4528e3684f1eacbc0e4481d0bf20ef&imgtype=0&src=http%3A%2F%2Fbbs.cnlinfo.net%2Fup%2Ftou%2F150611164743.jpg', // 头像地址
						userName: '小飞飞', // 用户名
						concernFlag: false, // 是否关注
						content: {
							title: '飞飞风景好，耶耶耶', // 内容标题
							type: 'img', // 内容类型，img代表图片，video代表视频
							imgUrl: 'https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=3313838802,2768404782&fm=26&gp=0.jpg', // 图片地址
							video: {
								previewUrl: '', // 预览图片地址
								viewCounts: '20w', // 播放量
								duration: '2:18' // 视频时长
							}
						},
						attitude: {
							attitudeFlag: 0, // 0表示未发表喜恶，1表示喜欢，2表示厌恶
							likeNum: 16, // 喜欢数量
							disgustNum: 1 // 厌恶数量
						},
						commentNum: 54, // 评论数量
						transmitNum: 13 // 转发数量
					}
				],
				[
					{
						lconUrl: 'http://pic1.zhimg.com/50/v2-af12f7b6f7eb2f2f5f7e2f3b7880cf01_hd.jpg', // 头像地址
						userName: '科技', // 用户名
						concernFlag: false, // 是否关注
						content: {
							title: '动次打次抖抖抖', // 内容标题
							type: 'video', // 内容类型，img代表图片，video代表视频
							imgUrl: '', // 图片地址
							video: {
								previewUrl: 'http://img2.imgtn.bdimg.com/it/u=2973939870,266577806&fm=26&gp=0.jpg', // 预览图片地址
								viewCounts: '17854 ', // 播放量
								duration: '2:18' // 视频时长
							}
						},
						attitude: {
							attitudeFlag: 0, // 0表示未发表喜恶，1表示喜欢，2表示厌恶
							likeNum: 72, // 喜欢数量
							disgustNum: 3 // 厌恶数量
						},
						commentNum: 166, // 评论数量
						transmitNum: 56 // 转发数量
					},
					{
						lconUrl:
							'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1581537044717&di=1d4528e3684f1eacbc0e4481d0bf20ef&imgtype=0&src=http%3A%2F%2Fbbs.cnlinfo.net%2Fup%2Ftou%2F150611164743.jpg', // 头像地址
						userName: '小飞飞', // 用户名
						concernFlag: false, // 是否关注
						content: {
							title: '飞飞风景好，耶耶耶', // 内容标题
							type: 'img', // 内容类型，img代表图片，video代表视频
							imgUrl: 'https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=3313838802,2768404782&fm=26&gp=0.jpg', // 图片地址
							video: {
								previewUrl: '', // 预览图片地址
								viewCounts: '20w', // 播放量
								duration: '2:18' // 视频时长
							}
						},
						attitude: {
							attitudeFlag: 0, // 0表示未发表喜恶，1表示喜欢，2表示厌恶
							likeNum: 16, // 喜欢数量
							disgustNum: 1 // 厌恶数量
						},
						commentNum: 54, // 评论数量
						transmitNum: 13 // 转发数量
					}
				]
			],
			// 顶部导航栏数据
			tabBarList: [
				{
					name: '关注',
					id: '1'
				},
				{
					name: '推荐',
					id: '2'
				},
				{
					name: '体育',
					id: '3'
				},
				{
					name: '热点',
					id: '4'
				},
				{
					name: '财经',
					id: '5'
				},
				{
					name: '娱乐',
					id: '6'
				},
				{
					name: '科技',
					id: '7'
				}
			],
			// 内容区高度
			tabHeight:0,
			// 当前所在页面
			current:1
		};
	},
	onLoad() {
		uni.getSystemInfo({
			success: rec => {
				this.tabHeight = rec.windowHeight - uni.upx2px(100)-50
				console.log(rec.windowHeight)
				console.log(rec.screenHeight)
				
			}
		})
	},
	methods:{
		swiperChange(e){
			this.current = e.detail.current
		}
	}
};
</script>

<style lang="scss" scoped>
	
</style>
