<!-- 首页 -->
<template>
	<view class="index">
		<tab-bar :list="tabBarList" :active="current" @swiperChange="swiperChange"></tab-bar>

		<view class="uni-tab-bar">
			<swiper class="swiper-box" :style="{ height: tabHeight + 'px' }" @change="swiperChange" :current="current">
				<swiper-item v-for="(list, index) in lists" :key="index">
					<scroll-view scroll-y class="list" lower-threshold="-50" @scrolltolower="scrolltolower(index)">
						<block v-for="(item, index1) in list.list" :key="index1">
							<card :item="item" :index="index" :index1="index1" @tapConcern="tapConcern" @tapAttitude="tapAttitude"></card>
						</block>
						<load-more :loadText="list.loadText"></load-more>
					</scroll-view>
				</swiper-item>
			</swiper>
		</view>
	</view>
</template>

<script>
import card from '../../components/card.vue';
import tabBar from '../../components/tabbar.vue';
import loadMore from '../../components/load-more.vue';
export default {
	components: {
		card,
		tabBar,
		loadMore
	},
	data() {
		return {
			// 信息数据
			lists: [
				{
					loadText:"上拉加载更多",
					list: [
						{
							lconUrl: 'http://pic1.zhimg.com/50/v2-af12f7b6f7eb2f2f5f7e2f3b7880cf01_hd.jpg', // 头像地址
							userName: '关注', // 用户名
							concernFlag: true, // 是否关注
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
								attitudeFlag: 1, // 0表示未发表喜恶，1表示喜欢，2表示厌恶
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
								attitudeFlag: 2, // 0表示未发表喜恶，1表示喜欢，2表示厌恶
								likeNum: 16, // 喜欢数量
								disgustNum: 1 // 厌恶数量
							},
							commentNum: 54, // 评论数量
							transmitNum: 13 // 转发数量
						}
					]
				},
				{
					loadText:"上拉加载更多",
					list: [
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
					]
				},
				{
					loadText:"上拉加载更多",
					list: [
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
					]
				},
				{
					loadText:"上拉加载更多",
					list: [
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
					]
				},
				{
					loadText:"上拉加载更多",
					list: [
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
					]
				},
				{
					loadText:"上拉加载更多",
					list: [
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
					]
				},
				{
					loadText:"上拉加载更多",
					list: [
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
				}
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
			tabHeight: 0,
			// 当前所在页面
			current: 1
		};
	},
	onLoad() {
		uni.getSystemInfo({
			success: rec => {
				this.tabHeight = rec.windowHeight - uni.upx2px(100) - 50;
			}
		})
	},
	onNavigationBarSearchInputClicked(){
		uni.navigateTo({
			url:"../search/search"
		})
		
	},
	onNavigationBarButtonTap(e) {
		if(e.index == 1){
			uni.navigateTo({
				url:"../add-input/add-input"
			})
		}
	},
	methods: {
		swiperChange(e) {
			this.current = e.detail.current;
		},
		// 更改关注状态
		tapConcern(i, i1) {
			this.lists[i][i1].concernFlag = !this.lists[i][i1].concernFlag;
		},
		// 顶踩功能
		tapAttitude(v) {
			if (this.lists[v.index][v.index1].attitude.attitudeFlag == v.attitudeFlag) {
				if (v.attitudeFlag == 1) {
					this.lists[v.index][v.index1].attitude.likeNum--;
				} else {
					this.lists[v.index][v.index1].attitude.disgustNum--;
				}
				this.lists[v.index][v.index1].attitude.attitudeFlag = 0;
				return;
			}

			if (v.attitudeFlag == 1) {
				if (!this.lists[v.index][v.index1].attitude.attitudeFlag == 0) {
					this.lists[v.index][v.index1].attitude.disgustNum--;
				}
				this.lists[v.index][v.index1].attitude.likeNum++;
			} else {
				if (!this.lists[v.index][v.index1].attitude.attitudeFlag == 0) {
					this.lists[v.index][v.index1].attitude.likeNum--;
				}
				this.lists[v.index][v.index1].attitude.disgustNum++;
			}
			this.lists[v.index][v.index1].attitude.attitudeFlag = v.attitudeFlag;
		},
		// 上拉更新
		scrolltolower(i){
			if(this.lists[i].loadText != "上拉加载更多" ){return}
			this.lists[i].loadText = "加载中..." 
			setTimeout(() =>{
				let obj = JSON.parse(JSON.stringify(this.lists[i].list[0]))
				this.lists[i].list.push(obj)
				// console.log(JSON.stringify(this.lists[i].list))
				this.lists[i].loadText = "上拉加载更多" 
			},1500);
		}
	}
};
</script>

<style lang="scss" scoped>
	
</style>
