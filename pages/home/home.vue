<template>
	<view :style="{height:windowHeight+'px'}" class=".flex_co outer">
		<view class=".flex_co usrInfo_box" :style="{height:view1+'px'}">
			<text class="title">我的</text>
			<view class="user_image ">
				<image src="" mode=""></image>
			</view>
			<view class="  flex_al flex_co">
				<text class="user_name ">TTTT</text>
				<text class="user_basement ">大数据 软工 20202120</text>			
			</view>
			<button class="btn_update " @click="show=!show">编辑信息</button>
		</view>
		<!-- 编辑蒙版 -->
		<van-popup :show="show " bind:close="onClose">
			<button @click="show=false">确定</button>
		</van-popup>
		<view class="other_info" :style="{height:view2+'px'}">
			<ul>
				<li>
					<text class="iconfont icon-dingdanliebiao"></text>订单
				</li>
				<li>
					<text class="iconfont icon-xinyong"></text>信用分
				</li>
				<li @click="goto">
					<text class="iconfont icon-wuliu" ></text>物流查询
				</li>
				<li>
					<text class="iconfont icon-yue1"></text>余额
				</li>
				<li>
					<text class="iconfont icon-bangzhu"></text>帮助与安全
				</li>
			</ul>
		</view>
		<view class="logOut">
			<li>
				<text class="iconfont icon-tuichu"></text>退出
			</li>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
					windowHeight:0,
					view1:0,
					view2:0,
					// 蒙版
					show:false
			};
		},
		methods:{
			goto(){
				uni.navigateTo({
					url:'/subpages/wuliuchaxun/wuliuchaxun'
				})
			}
		},
		onLoad() {
			let _this=this
			uni.getSystemInfo({
				success(res) {
					_this.windowHeight=res.windowHeight;
					_this.view1=Math.floor(res.windowHeight*0.4);
					_this.view2=Math.floor(res.windowHeight*0.4);
				}
			})
		}
	}
</script>

<style lang="scss">
page{
	padding-bottom: 20rpx;
	color: white;
	font-size: 16px;
	background-color: #5b4cd5;
}
.flex_co{
	display: flex;
	flex-direction: column;
	justify-content: space-between;
}
.margin_bo{
	margin-bottom: 20rpx;
}
.flex_al{
	display: flex;
	align-items: center;
}
// 样式开始
.outer{
	display: flex;
	justify-content: space-between;
	.usrInfo_box{
		padding-top: 20rpx;
		margin: 0 auto;
		width: 600rpx;
		align-items: center;
		.title{
			font-size: 50rpx;
			margin-bottom: 30rpx;;
		}
		.user_image{
			width: 240rpx;
			height: 240rpx;
			background-color: aliceblue;
			border-radius: 60rpx;
			image{
				height: 100%;
				width: 100%;
			}
			
		}
		.btn_update{
		
			width: 320rpx;
		
			background-color: #ffb94f;
			height: 80rpx;
			color: white;
			line-height:80rpx;
			border-radius: 40rpx;
		}
	}
	.other_info{	
		padding: 0rpx 40rpx 0rpx 40rpx;
		ul{
			height: 100%;
			display: flex;
			flex-direction: column;
			justify-content: space-between;
			li{
			
			}
		}
	}
	.logOut{
		padding-left: 40rpx;
		padding-bottom: 50rpx;
	}
}
</style>
