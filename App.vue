<script>
	export default {
		onLaunch: function() {
			console.warn('当前组件仅支持 uni_modules 目录结构 ，请升级 HBuilderX 到 3.1.0 版本以上！')
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

<style lang="scss">
    @import "/wxcomponents/dist/common/index.wxss";
	// icon图标
	@import './static/me/iconfont.css';
	/*每个页面公共css */
	@import '@/uni_modules/uni-scss/index.scss';
	/* #ifndef APP-NVUE */
	@import '@/static/customicons.css';
	// 设置整个项目的背景色
	page {
		background-color: #ffffff;
	}
	/* #endif */
	// 隐藏滚动条
	/* #ifdef MP-WEIXIN || APP-PLUS */
			::-webkit-scrollbar {
			    display: none;
			    width: 0 !important;
			    height: 0 !important;
			    -webkit-appearance: none;
			    background: transparent;
			    color: transparent;
			  }
		/* #endif */
	
</style>
