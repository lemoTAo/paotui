<template>
	<view class="outer">
		<view class="option_box">
			<view class="opton_card">
				<text v-for="item,index in list" :key="index" @click="changeActive(index)" :class="[index==active?'boder_bottom':'']">{{item}}</text>
			</view>
		</view>
		<view class="detail_message flex_c">
			<view class="detail_box">
				<view class="detail_image">
					<image src="@/static/order/packages.png" mode=""></image>
				</view>
				<view class="flex_c detail_code">
					<text>编码 ：3028</text>
					<text>2020年10月22日 南三门</text>
				</view>
				<view class="detail_price">
					<text>￥55</text>
				</view>
			</view>
			<view class="detail_box">
				<view class="detail_image">
					<image src="@/static/order/packages.png" mode=""></image>
				</view>
				<view class="flex_c detail_code">
					<text>编码 ：3028</text>
					<text>2020年10月22日 南三门</text>
				</view>
				<view class="detail_price">
					<text>￥55</text>
				</view>
			</view>
			<view class="detail_box">
				<view class="detail_image">
					<image src="@/static/order/packages.png" mode=""></image>
				</view>
				<view class="flex_c detail_code">
					<text>编码 ：3028</text>
					<text>2020年10月22日 南三门</text>
				</view>
				<view class="detail_price">
					<text>￥55</text>
				</view>
			</view>
			
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list:['全部','待完成','已完成','待评价','已退款'],
				active:0
			}
		},
		methods: {
			changeActive(e){
				this.active=e
			}
		}
	}
</script>

<style lang="scss">
	.flex_c{
		display: flex;
		flex-direction: column;
	}
	.boder_bottom{
		border-bottom: 5px solid #6d60da;
	}
.outer{
	font-size: 32rpx;
	padding: 0 30rpx;
	.option_box{
		display: flex;

	     .opton_card{
	     		display: flex;
				width: 100%;
	     		justify-content: space-between;
			
	      }	
	}
	.detail_message{
		padding-top: 40rpx;
		.detail_box{
			margin-top: 20px;
			background-color: #e6f3f8;
			border-radius: 30rpx;
			display: flex;
			justify-content: flex-start;
			height: 100rpx;
			padding: 40rpx;
			.detail_image{
				height: 100rpx;
				width: 100rpx;
				margin-right: 40rpx;
				image{
					height: 100%;
					width: 100%;
				}
			}
			.detail_code{
				margin-right: 40rpx;
				justify-content: space-between;
				
				text{
					&:nth-child(2){
						color: darkgray;
					   	font-size: 26rpx;
					}
				}
			}
			.detail_price{
				display: flex;
				flex-direction: column;
				justify-content: center;
				 margin-left: auto;
			}
		}
		
	}
}
</style>
