<template>
	<view class="outer" :style="{ height: windowHeight + 'px' }">
		<view class="address-box flex_ro_b" :style="{ height: view1 + 'px' }">
			<view class="flex_co item-left">
				<text>我的地址</text>
				<text>C区超市12333asgf</text>
			</view>
			<view class="">
				<uni-icons type="compose" size="25"></uni-icons>
			</view>
		</view>
		<view class="item flex_co " :style="{ height: view2 + 'px' }">
			<view class="flex_co flex_row">
				<view class="">
					<view class="item-image-box">
						<view class="item-image">
							<image src="@/static/order_rec/round.png">
							</image>
						</view>
					</view>
					<view class="flex_co">
						<text>快递代取</text>
						<text>快递超市</text>
						<text>$12</text>
					</view>
				</view>
			</view>
			<button class="btn" @click="goto">决定接单</button>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			windowHeight: 0,
			view1: 0,
			view2: 0
		};
	},
	methods: {
		goto(){
			uni.navigateTo({
				url:'/subpages/order_finish/order_finish?Index='+1
			})
		}
	},
	onLoad() {
		let _this = this;
		uni.getSystemInfo({
			success(res) {
				_this.windowHeight = res.windowHeight;
				_this.view1 = Math.floor(res.windowHeight * 0.12);
				_this.view2 = Math.floor(res.windowHeight * 0.7);
			}
		});
	}
};
</script>

<style lang="scss">
page {
}
.flex_co {
	display: flex;
	flex-direction: column;
	justify-content: space-between;
}
.flex_row{
	display: flex;
	flex-direction: column;
	justify-content: center;
	align-items: center;
}
.flex_ro_b{
	display: flex;
	justify-content: space-between;
}
.outer {
	.address-box {
		width: 100%;
		padding: 30rpx 40rpx;
		color: white;
		font-size: 30rpx;
		font-weight: 600;
		background-color: #6f6ef4;
		box-sizing: border-box;
		.item-left{
			width: 600rpx;
			height: 100%;
			text {
			&:last-child {
				height:60rpx;
				font-size: 40rpx;
			}
		   }
		}
		
	}
	.item {
		padding: 40rpx 50rpx;
		font-size: 40rpx;
		font-weight: 300;
		margin: 20rpx 0;
		display: flex;
		justify-content: space-between;
		box-sizing: border-box;
		.item-image-box {
			display: flex;
			flex-direction: column;
			justify-content: center;
			width: 420rpx;
			height: 420rpx;
			border-radius: 50rpx;
			align-items: center;
			background-color: #ebebff;
			.item-image {
				height:180rpx;
				width: 180rpx;
				image {
					height: 100%;
					width: 100%;
				}
			}
		}
		text {
			margin-top: 16rpx;
			&:last-child {
				font-weight: 800;
			}
		}
	}
	.btn {
		width: 50%;
		height: 90rpx;
		background-color: #655cf3;
		color: white;
		border-radius: 40rpx;
	}
}
</style>
