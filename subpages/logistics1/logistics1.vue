<template>
	<view class="flex_c outer" :style="{ height: windowHeight + 'px' }">
		<!-- address -->
		<view class="address-box flex_r">
			<view class="address flex_c">
				<text>我的地址</text>
				<text>{{address}}</text>
			</view>
			<view class="address_icon .flex_c_ce" @click="show=!show; UpdateAddress=address"><uni-icons type="compose" size="25"></uni-icons></view>
		</view>
		<!-- 修改地址蒙版 -->
		<van-popup :show="show" bind:close="onClose">
			<text>我的地址:</text>
			<input type="text" v-model="UpdateAddress">
			<button @click="show=false" size="mini">取消</button>
			<button @click="show=false;address=UpdateAddress" size="mini">确定</button>
		</van-popup>
		<!-- jianshuu  -->
		<view class="express_number flex_r ">
			<view class="express_left flex_r_st">
				<view class="image_box .flex_c_ce"><image src="/static/index/packages.png"></image></view>
				<text>快递</text>
			</view>
			<view class="express_right .flex_r_st">
				<button @click="jiajian('jian')">-</button>
				<input type="text" @blur="inputContanin($event)" :value="number_sum" >
				<button @click="jiajian('jia')">+</button>
			</view>
		</view>
		<!-- detail -->
		<view class="detail .flex_c">
			<view class="option-item flex_c">
				<text class="item">编号</text>
				<text>55663</text>
			</view>
			<view class="flex_r">
				<view class="option-item flex_c">
					<text class="item">下单者</text>
					<text>陶文杰</text>
				</view>
				<view class="option-item flex_c">
					<text class="item">联系方式</text>
					<text>5566346485</text>
				</view>
			</view>
			<view class="">
				<view class="option-item flex_c">
					<text class="item">取件地址</text>
					<text>C区c4快递超市</text>
				</view>
			</view>
		</view>
		<!-- size -->
		<view class="size_box flex_c">
			<text>尺寸选择</text>
			<view class="flex_r_st">
				<view class="item flex_c" v-for="(item, index) in choseSize" :key="index" @click="changActive(index)">
					<view class="image_box" :class="[index == Active ? 'box-shadow' : '']"></view>
					<text>{{ item.size }}</text>
					<text>￥{{ item.price }}</text>
				</view>
			</view>
		</view>
		<!-- 下一步 -->
		<view class="next flex_c">
			<view class="urgent_service flex_r">
				<view class="item-left">加急服务</view>
				<view class="item-right .flex_r_st">
					<text class=".flex_c_ce">需要格外自定义金钱</text>
					<view class="icon" @click="chageIcon" :class="[icon ? 'iconAcvtive' : '']"></view>
				</view>
			</view>
		</view>
		<button class="btn" @click="goto">下一步</button>
	</view>
</template>
<script>
export default {
	data() {
		return {
			windowHeight: 0,
			// 加急服务
			icon: false,
			// 尺寸选择
			Active: 0,
			address:'重庆移通学院',
			UpdateAddress:'',
			number_sum: 1,
			timer: null,
			show:false,
			choseSize: [
				{
					size: '小件',
					price: 3
				},
				{
					size: '中件',
					price: 5
				},
				{
					size: '大件',
					price: 10
				}
			]
		};
	},
	onLoad() {
		let _this = this;
		uni.getSystemInfo({
			success(res) {
				_this.windowHeight = res.windowHeight;
			}
		});
	},
	methods: {
		chageIcon() {
			this.icon = !this.icon;
		},
		changActive(e) {
			this.Active = e;
		},
		inputContanin(e) {
			
		},
		jiajian(e) {
			if (e === 'jian') {
				if (this.number_sum === 1) return;
				this.number_sum--;
			} else {
				this.number_sum++;
			}
		},
		goto() {
			uni.navigateTo({
				url: '/subpages/pay/pay'
			});
		}
	}
};
</script>
<style lang="scss" scoped>
.box-shadow {
	box-shadow: 10rpx 15rpx 6rpx #bfbfbf;
}
.flex_c {
	display: flex;
	justify-content: space-between;
	flex-direction: column;
}
.flex_c_ce {
	display: flex;
	justify-content: center;
	align-items: center;
	flex-direction: column;
}
.flex_c_s {
	display: flex;
	justify-content: flex-start;
	align-items: center;
	flex-direction: column;
}
.flex_r {
	display: flex;
	justify-content: space-between;
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
.iconAcvtive {
	border: 2px solid #584cdf !important;
	background-color: #584cdf !important;
}
.outer {
	padding: auto 0;
	.address-box {
		padding: 25rpx;
		background-color: #6f6df4;
		.address {
			color: white;
			text {
				&:first-child {
					font-weight: 600;
					margin-bottom: 10rpx;
				}
				&:last-child {
					font-size: 42rpx;
					font-weight: 800;
				}
			}
		}
	}
	.express_number {
		padding: 0 30rpx;
		margin: auto 0;
		height: 180rpx;
		.express_left {
			font-size: 40rpx;
			.image_box {
				height: 80px;
				width: 80px;
				background-color: #e4f2f8;
				border-radius: 20px;
				image {
					height: 50%;
					width: 50%;
				}
			}
			& > text {
				margin-left: 20rpx;
			}
		}
		.express_right {
			button {
				padding: 0;
				width: 30px;
				height: 30px;
				line-height: 30px;
				text-align: center;
				border: 1px solid #c0c3c7;
			}
			input {
				text-align: center;
				margin: 0 10px;
				height: 30px;
				width: 50px;
				border-radius: 10px;
				border: 1px solid #c0c3c7;
			}
		}
	}
	.detail {
		margin: auto 30rpx;

		padding: 30rpx 60rpx;
		height: 200px;
		background-color: #6f6df4;
		border-radius: 20px;
		.option-item {
			color: #ffffff;
			font-size: 36rpx;
			.item {
				color: #b3adfa;
				font-size: 28rpx;
				margin-bottom: 10px;
			}
		}
	}
	.size_box {
		margin: auto 30rpx;
		text {
			&:first-child {
				font-size: 40rpx;
			}
		}
		.item {
			margin-top: 20rpx;
			margin-right: 10px;
			.image_box {
				width: 120rpx;
				height: 120rpx;
				margin-bottom: 10px;
				border-radius: 20rpx;
				background-color: #6f6df4;
			}
		}
	}
	.next {
		margin: auto 35rpx;
		.urgent_service {
			.item-left {
				font-size: 40rpx;
			}
			.item-right {
				font-size: 22rpx;
				color: #c0c3c7;
				.icon {
					width: 20px;
					height: 20px;
					padding: 1px;
					margin-left: 10rpx;
					box-sizing: border-box;
					border: 2px solid lightgray;
					border-radius: 20px;
					color: #6f6df4;
					background-color: lightgray;
					background-clip: content-box;
				}
			}
		}
	}
	.btn {
		margin: auto auto;
		margin-bottom: 20px;
		color: white;
		background-color: #7270f3;
		border-radius: 20px;
		width: 60%;
	}
}
</style>
