<template>
	<view class="outer .flex_c_s" :style="{ height: windowHeight + 'px' }">
		<view class="detail_box .flex_r_st">
			<view class="detail-item flex_c">
				<text>编号</text>
				<text>568759</text>
			</view>
			<view class="detail-item flex_c">
				<text>地址</text>
				<text>C区C4快递超市</text>
			</view>
		</view>

		<view class="process-box ">
			<text class="proces-text">进度</text>
			<view class="process-contanter .flex_c_ce">
				<view class="Dotted-line"></view>
				<view class="process-list ">
					<view class="process-item .flex_st">
						<view class="image-box"></view>
						<view class="text-item flex_c">
							<text>确认收货</text>
							<text class="text">12.08.22022-6.30 pm</text>
						</view>
					</view>
				</view>
				<view class="process-list ">
					<view class="process-item .flex_st">
						<view class="image-box"></view>
						<view class="text-item flex_c">
							<text>确认收货</text>
							<text class="text">12.08.22022-6.30 pm</text>
						</view>
					</view>
				</view>
				<view class="process-list ">
					<view class="process-item .flex_st">
						<view class="image-box"></view>
						<view class="text-item flex_c">
							<text>确认收货</text>
							<text class="text">12.08.22022-6.30 pm</text>
						</view>
					</view>
				</view>
			</view>
			<view class="map-container">
				<view class="map"></view>
			</view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			windowHeight: 0
		};
	},
	onLoad() {
		let _this = this;
		uni.getSystemInfo({
			success(res) {
				_this.windowHeight = Math.floor(res.windowHeight * 0.9);
			}
		});
	}
};
</script>

<style lang="scss">
.flex_c {
	display: flex;
	justify-content: space-between;
	flex-direction: column;
}
.flex_c_ce {
	display: flex;
	justify-content: center;
	flex-direction: column;
}
.flex_c_s {
	display: flex;
	justify-content: flex-start;
	flex-direction: column;
}
.flex_st {
	display: flex;
	align-items: center;
	justify-content: flex-start;
}
.flex_r_no {
	display: flex;
	justify-content: center;
}
.flex_r_st {
	display: flex;
	align-items: center;
	justify-content: flex-start;
}
.text {
	font-size: 26rpx;
	color: #797b7e;
}
.outer {
	padding: 40rpx 40rpx;
	box-sizing: border-box;
	.detail_box {
		padding: 50rpx 40rpx;
		height: 200rpx;
		color: #ecebfe;
		border-radius: 30rpx;
		background-color: #6154f5;
		box-sizing: border-box;
		.detail-item {
			height: 100%;
			margin-right: 40rpx;
			font-size: 26rpx;
			text {
				&:last-child {
					font-size: 34rpx;
				}
			}
		}
	}
	.process-box {
		margin: auto 0;
		.proces-text {
			font-size: 44rpx;
		}
		.process-contanter {
			position: relative;
			margin-top: 40rpx;
			.Dotted-line {
				position: absolute;
				width: 1px;
				height: 600rpx;
				top: 0;
				left: 50rpx;
				border-left: 2px dashed #b7b3ed;
			}
			.process-list {
				.process-item {
					height: 65px;
					margin-bottom: 40rpx;
					box-sizing: border-box;
					.image-box {
						width: 60px;
						height: 60px;
						margin-right: 20px;
						border-radius: 50%;
						background-color: #6154f5;
						background-image: url('/static//logis/组 59.png');
						background-repeat: no-repeat;
						background-size: 60% 60%;
						background-position: center;
						z-index: 1;
					}
					.text-item {
						padding: 20rpx 0;
						height: 100%;
						box-sizing: border-box;
					}
				}
				
			}
		}
	    .map-container {
			position: relative;
			width: 100%;
			height: 300rpx;
			z-index: 999;
					.map {
						position: absolute;
						top: 0;
						width: 80%;
						right: 0;
						height: 300rpx;
						background-color: #b7b3ed;
						z-index: 9999;
					}
				}
	}
}
</style>
