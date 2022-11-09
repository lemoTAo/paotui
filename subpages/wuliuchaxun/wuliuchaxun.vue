<template>
	<view :style="{height:windowHeight+'px'}" class="outer .flex_c_s">
		<view class="top_box .flex_c_s" >
			<view class=".flex_c_ce">
				<view class="flex_r_no">
					<uni-icons type="location-filled"></uni-icons>
					<view class="">重庆移通学院C区</view>
					<uni-icons type="bottom"></uni-icons>
				</view>
				<view class="image_box .flex_c_s">
					<text>物流查询</text>
					<text>请在下方输入你的订单号</text>
					<input type="text" class="input_style">
				</view>
			</view>
		</view>
		<view class="bottom-box flex_c" :style="{height:view2+'px'}">
			<text class="text">类型</text>
			<view class="flex_r kuaidi_box">
				<view class=" type_box ">
					<view class="flex_c item">
						<view class="image_box">
						</view>
						<text>快递</text>
						<text>快速下单，立马就到</text>
					</view>
				</view>
				<view class=" type_box ">
					<view class="flex_c item">
						<view class="image_box">
						</view>
						<text>快递</text>
						<text>快速下单，立马就到</text>
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
				windowHeight:0,
				view1:0,
				view2:0
			};
		},
		onLoad() {
			let _this=this
			uni.getSystemInfo({
				success(res) {
					_this.windowHeight=res.windowHeight*0.95;
					_this.view1=Math.floor(res.windowHeight*0.55);
					_this.view2=Math.floor(res.windowHeight*0.35);
				}
			})
		},
		methods:{
			
		}
	}
</script>

<style lang="scss">
.flex_c{
	display: flex;
	justify-content: space-between;
	flex-direction: column;
}
.flex_c_ce{
	display: flex;
	justify-content: center;
	align-items: center;
	flex-direction: column;
}
.flex_c_s{
	display: flex;
	justify-content: flex-start;
	align-items: center;
	flex-direction: column;
}
.flex_r{
	display: flex;
	justify-content: space-between;
}
.flex_r_no{
	display: flex;
	justify-content: center;
}
.outer{
	box-sizing: border-box;
	padding: 0 60rpx;
	.top_box{
		box-sizing: border-box;
		.image_box{
			margin-top: 20px;
			width: 640rpx;
			height: 600rpx;
			border-radius: 40px;
			background: linear-gradient(to bottom right,blue, pink);
			// background-image:url('/static/wuliuchaxun/Illustration.png');
			text{
				margin-top: 20px;
				&:first-child{
					font-size: 40rpx;
					color:white;
					font-weight: 700;
				}
				&:nth-child(2){
					color: #ada6fa;
					font-size: 26rpx;
				}
			}
			.input_style{
				margin-top: 40rpx;
				padding-left: 70rpx;
				width: 200px;
				height: 40px;
				line-height: 40px;
				background: url('/static/wuliuchaxun/组 18.png') no-repeat 10px 25rpx ;
				background-color: white;
				border-radius: 10px;
				box-sizing: border-box;
			}
		}
	}
	.bottom-box{
		box-sizing: border-box;
		width: 100%;
		.text{
			margin: 40rpx 0 ;
			&:first-child{
				font-size: 30px;
			}
		}


			.type_box{
				
				.item{
					box-sizing: border-box;
					padding: 30rpx 0;
					align-items: center;
				width: 290rpx;
				height: 300rpx;
				border-radius: 50rpx;
				background-color: #eeeefa;
				.image_box{
					height: 100rpx;
					width: 100rpx;
					background-color: #ada6fa;
				}
				text{
					&:last-child{
						font-size: 26rpx;
						color: #b8b8c1;
					}
				}
			   }
			}

			
			
		}
	
}
</style>
