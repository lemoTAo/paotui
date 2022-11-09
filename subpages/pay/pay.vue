<template>
	<view class="outer flex_co">
		<view class="text_box_">
			<text>支付方式</text>
		</view>
		
		<view class="pay_way_box ">
			<view class=" item flex_row" 
			:class="[active==0?'bkActive':'']"
			@click="changeActive(0)"
			>
				<view class="image_box">
					
				</view>
				<view class="flex_co text_box">
					<text>支付宝</text>
					<text>12345678911</text>
				</view>
				<view class="dian_box">
					<view class="dian" :class="[active==0?'dianActive':'']">
						
					</view>
				</view>
			</view>
			<view class=" item flex_row" 
			:class="[active==1?'bkActive':'']" 
			@click="changeActive(1)">
				<view class="image_box">
					
				</view>
				<view class="flex_co text_box">
					<text>支付宝</text>
					<text>12345678911</text>
				</view>
				<view class="dian_box">
					<view class="dian" :class="[active==1?'dianActive':'']">
						
					</view>
				</view>
			</view>
			<view class=" item flex_row"
			 :class="[active==2?'bkActive':'']"
			 @click="changeActive(2)">
				<view class="image_box">
					
				</view>
				<view class="flex_co text_box">
					<text>支付宝</text>
					<text>12345678911</text>
				</view>
				<view class="dian_box">
					<view class="dian" :class="[active==3?'dianActive':'']">
						
					</view>
				</view>
			</view>
		</view>
		<button class="btn" @click="goto()">确认</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				active:0
			};
		},
		methods:{
			changeActive(e){
				this.active=e
			},
			goto(){
				uni.navigateTo({
					url:'/subpages/order_finish/order_finish?Index='+0
				})
			}
		}
	}
</script>

<style lang="scss">
.bkActive{
	background-image: linear-gradient(
	to right, #679ae7 ,#655cf4
	)!important;
}
.dianActive{
	background-color: white;
	background-clip: content-box;
}
.flex_row{
	display: flex;
	justify-content: space-between;
}
.flex_co{
	display: flex;
	flex-direction: column;
	justify-content: space-between;
}
.outer{
     padding: 0 40rpx;	
	 .text_box_{
		margin-top: 20px; 
	 }
	 .pay_way_box{
		.item{
		margin-top: 20px;
		height: 160rpx;
		padding: 30rpx 40rpx;
		background-color: #f6f5fd;
		border-radius: 40rpx;
		box-sizing: border-box;
		.image_box{
			width: 100rpx;
			height: 100rpx;
			background-image: url('/static/pay/图层 3.png');
			background-size:100% 100% ;
			image{
				width: 100%;
				height: 100%;
			}
		}
		.text_box{
			text{
				&:last-child{
					font-size: 26rpx;
					color: darkgray;
				}
			}
		}
		.dian_box{
			display: flex;
			flex-direction: column;
            justify-content: center;			
			.dian{
			height: 30rpx;
			width: 30rpx;
			padding: 3px;
			border: 1px solid #d7d3f5;
			border-radius: 100%;
		  }
		}
		
	    }
	 }
	 .btn{
		 margin-top: 70px;
		 width: 200px;
		 height: 50px;
		 color: white;
		 background-color: #665ef5;
		 border-radius: 25px;
	 }
    

}
</style>
