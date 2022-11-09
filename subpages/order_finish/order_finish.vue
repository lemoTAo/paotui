<template>
	<view class="outer" >
		<view class="local_loked" :style="{height: windowHeight+'px'}">
			<view >
			</view>
			<view class="image_box flex_co">
				<text>{{obj[Index].title}}</text>
			</view>
			<button class="btn" @click="goto(obj[Index].url)">{{obj[Index].btn}}</button> 
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				windowHeight:0,
				Index:0,
				obj:[
					{
						title:'支付成功',
						btn:'返回首页',
						url:'/page/index/index'
					},
					{
						title:'接单成功',
						btn:'请尽快配送',
						url:'/page/index/index'
					}
				]
			};
		},
		onLoad(res) {
			this.Index=parseInt(res.Index)
			let _this=this
			uni.getSystemInfo({
				success(res) {
					_this.windowHeight=Math.floor(res.windowHeight*0.5)
				}
			})
		},
		methods:{
			goto(url){
				console.log(url)
				uni.switchTab({
					url:'/pages/index/index'
				});
			}
		}
	}
</script>

<style lang="scss" scoped>
.flex_co{
	display: flex;
	align-items: center;
	justify-content: center;
	flex-direction: column;
}
.outer{
	box-sizing: border-box;
	padding: 0 100rpx;
	.local_loked{
		width: 500rpx;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: space-between;
		.image_box{
			font-size: 40rpx;
			font-weight: 600;
			color:white;
			
			width: 300rpx;
			height: 300rpx;
			border-radius: 150rpx;
			background-color: #684deb;
		}
		.btn{
			width: 80%;
			height: 90rpx;
			line-height: 90rpx;
			border-radius: 30rpx;
			color: #1b0f80;
		}
	}
	
	
	
}
</style>
