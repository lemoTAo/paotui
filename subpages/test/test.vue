<template>
	<view class="outer flex_co_be" :style="{ height: windowHeight + 'px' }">
		<view class="">
			<view class="big-item" v-for="item,index in list">
				<van-swipe-cell right-width="65">
					<van-cell-group>
						<!-- <van-cell title="单元格" value="内容" / -->
						<template>
							<view class=".flex_row">
								<view class="flex_r_st">
									<view class="iamge-box flex_co margin_right20"><image src="/static/order/packages.png"></image></view>
									<view class="flex_co ">
										<text class="text-bo-mr">{{item.name}}1</text>
										<text>{{item.number}}</text>
									</view>
								</view>
								<view class="flex_co">${{item.price}}</view>
							</view>
						</template>
					</van-cell-group>
					<view slot="right">
						<view class="icon-del-box flex_co" @click="deleitem(item.id)"><uni-icons type="trash" size="25"></uni-icons></view>
					</view>
				</van-swipe-cell>
			</view>
					
							
		</view>
		<view class="">
			<view class="info-box flex_row">
				<!-- zuo -->
				<view class="flex_co_be">
					<view class="item flex_r_st ">
						<view class="icon flex_co margin_right20"><image src="/static/路径 2579.png"></image></view>
						<text class="fonSize26">重庆</text>
					</view>
					<view class="item flex_r_st ">
						<view class="icon flex_co margin_right20"><image src="/static/路径 2579.png"></image></view>
						<text class="fonSize26">重庆</text>
					</view>
				</view>
				<!-- you -->
				<view class="flex_co">
					<view class="icon flex_co" style="background-color: #f0b861;"><image src="/static/Icon material-edit.png" mode=""></image></view>
				</view>
			</view>

			<view class="bottom-box flex_row">
				<view class="flex_co_be text-box">
					<text class="fonSize26">总共</text>
					<text>￥40.00</text>
				</view>
				<button class="btn">确认下单</button>
			</view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			windowHeight: 0,
			list:[
				{
					id:1,
					name:'快递1',
					number:'c4-15-12',
					price:12
				},
				{
					id:2,
					name:'快递2',
					number:'c4-12-22',
					price:5
				},
				{
					id:3,
					name:'快递3',
					number:'c4-8-9',
					price:16
				}
			]
		};
	},
	methods: {
		deleitem(id){
			this.list=this.list.filter(item=> item.id!=id)
		}
	},
	onLoad() {
		let _this = this;
		uni.getSystemInfo({
			success: res => {
				_this.windowHeight = res.windowHeight;
			}
		});
	}
};
</script>

<style lang="scss" scoped>
	.margin_right20 {
		margin-right: 20px;
	}
	.fonSize26 {
		font-size: 28rpx;
		color: white;
	}
	.flex_r_st {
		display: flex;
		justify-content: flex-start;
	}
	.flex_row {
		display: flex;
		justify-content: space-between;
	}
	.flex_co {
		display: flex;
		flex-direction: column;
		justify-content: center;
	}
	.flex_co_be {
		display: flex;
		flex-direction: column;
		justify-content: space-between;
	}
	.text-bo-mr{
		margin-bottom: 10px;
	}
.outer {
	.big-item {
		height: 80px;
		padding: 0 30rpx;
		margin-bottom: 10px;
		& text{
			&:last-child{
				font-size: 26rpx;
				color: #a2a2ab;
			}
		}
	}
	.icon-del-box {
		margin-top: 1px;
		width: 50px;
		height: 50px;
		align-items: center;
		border-radius: 50px;
		background-color: #fa4d62;
	}
	.info-box {
		margin: 0 40rpx;
		height: 230rpx;
		padding: 50rpx;
		margin-bottom: 50px;
		border-radius: 20px;
		background-color: #676cf0;
		.item {
			align-items: center;
			
		}
	}
	.bottom-box {
		margin: 0 40rpx;
		height: 200rpx;
		align-items: center;
		border-top: 1px solid #e6e6e6;
		.text-box {
			height: 100rpx;
			&>text{
				&:first-child{
					color: #ababab;
				}
			}
		}
		.btn {
			margin: 0;
			width: 50%;
			height: 100rpx;
			color: white;
			font-size: 13px;
			line-height: 100rpx;
			border-radius: 20px;
			background-color: #655cf3;
		}
	}
}
.icon {
	height: 40px;
	width: 40px;
	border-radius: 10px;
	align-items: center;
	background-color: #6156f4;
	image {
		width: 35%;
		height: 45%;
	}
}

.iamge-box {
	height: 80px;
	width: 80px;
	background-color: #e6f3f8;
	border-radius: 20px;
	align-items: center;
	box-sizing: border-box;
	image {
		width: 50%;
		height: 50%;
	}
}
</style>
