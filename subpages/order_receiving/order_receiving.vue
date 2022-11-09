<template >
	<view class="outer">
		<van-search shape="round"></van-search>
		<view class="flex_row">
			<view class="option-item" v-for="item,index in options"
			:key="index"
			:class="[active==index?'option_active':'']"
			@click="changeActive(index)"
			>{{item}}</view>
		</view>
		<view class="package-iten flex_row">
		
			<view class="item flex_co" 
			v-for="item,index in molist" :key="index"
			@click="goto(item)">
				<view class="item-image-box">
					<view class="item-image flex_co_c">		
							<image :src="item.imgUrl"></image>
					</view>
				</view>
				<text>{{item.title}}</text>
				<text>{{item.address}}</text>
				<text>${{item.price}}</text>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				options:[
					'全部',
					'最新',
					'附近'
				],
				active:0,
				molist:[
					{
						title:'快递代取',
						address:'南三门',
						imgUrl:'/static/order/packages.png',
						price:2
					},{
						title:'外卖代取',
						address:'南三门',
						imgUrl:'/static/order/food.png',
						price:2
					},{
						title:'快递代取',
						address:'南三门',
						imgUrl:'/static/order/packages.png',
						price:2
					},
					{
						title:'快递代取',
						address:'南三门',
						imgUrl:'/static/order/packages.png',
						price:2
					}
				]
			}
		},
		methods: {
			changeActive(index){
				this.active=index
			},
			goto(item){
				uni.navigateTo({
					url:'/subpages/jiedanpage/jiedanpage'
				})
			}
		},
		onLoad(Page) {
			console.log(Page)
		}
	}
</script>

<style lang="scss">
	page{
		font-size: 28rpx;
	}
.flex_row{
	display: flex;
	// justify-content: flex-start;
	flex-wrap: wrap;
}
.flex_co{
	display: flex;
	flex-direction: column;
	justify-content: space-between;
}
.flex_co_c{
	display: flex;
	flex-direction: column;
	justify-content: center;
}
.option_active{
	background-color: #655cf3 !important;
	color: white;
}
.outer{
	padding: 0 40rpx;
	.option-item{
		margin: 30rpx  20rpx 30rpx 0;
		background-color: #eeeeee;
		width: 120rpx;
		height: 50rpx;
		line-height: 50rpx;
		text-align: center;
		border-radius: 30rpx;
	}
	.package-iten{
			justify-content: space-between;
		.item{
			margin: 20rpx 0;
			display: flex;
			justify-content: space-between;
			.item-image-box{
				display: flex;
				flex-direction: column;
				justify-content: center;
				width: 300rpx;
				height: 300rpx;
				border-radius: 50rpx;
				align-items: center;
				background-color: #ebebff;
				.item-image{
					height: 140rpx;
					width: 140rpx;
					align-items: center;
					border-radius: 100%;
					background-color: #655cf3;
					image{
						height: 50%;
						width: 50%;
					}
				}
			}
			text{
				margin-top: 6rpx;
				&:last-child{
					font-weight: 800;
				}
			}
		}
	}
}
</style>
