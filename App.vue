<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style>
	/*每个页面公共css */
	/* 官方CSS文件 */
	@import './common/uni.css';
	/* 矢量图库 */
	@import './common/iconfont.css';
	/* 动画库 */
	@import './common/animate.css';
	/* 自定义公共CSS样式 */
	@import url("./common/common.css");
</style>
