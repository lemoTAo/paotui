<template>
	<view :style="{height:windowHeight+'px'}" class="outer"> 
		<view class="box1 flex-c" >
			<view class=" flex-row">
				<text style="font-size: 40rpx;">消息</text>
	
				<van-search shape="round" style="width: 70%;"></van-search>
				<uni-icons type="personadd"></uni-icons>
				<uni-icons type="plusempty"></uni-icons>
			</view>
			<scroll-view  scroll-x="true" class="scroll-view-content">

					<view class="dataList" 
					v-for="item,index in meassage_list" :key="index"
					@click="goto(item)">
		                    <view class="flex-c " >
		                        <view class="list">
							       <image src="/static/chat/IMG_-1.png" ></image>
							      	
							       </view>
							     <view>{{item.name}}</view>
		                    </view>
							
	
					</view>
				
	
			</scroll-view>
		</view>
		<view class="massage_list chang" 
		:style="{height:view2+'px'}" 
		>
			<scroll-view scroll-y="true" :style="{height:view2+'px'}" >
			
		        
				<view class="message_box" 
				v-for="item,index in meassage_list" :key="index"
				@click="goto(item)">
					<view class="message-item-left">
						<view class="item-image">
							<image src="/static/chat/IMG_-1.png" mode=""></image>
						</view>
						<view class="item-name">
							<view class="name">{{item.name}}</view>
							<text class="message">{{item.message}}</text>
						</view>
					</view>
					<view class="message-item-right">
						<text class="message_date">11</text>
					</view>
				</view>
			</scroll-view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			windowHeight:0,
			view2:0,
			view1:0,
			meassage_list:[
				{
					imageUrl:'',
					name:'张三',
					message:'hi',
					Date:'2022-11-1'
					
				},
				{
					imageUrl:'',
					name:'李四',
					message:'倒霉李四',
					Date:'2022-8-1'
					
				},
				{
					imageUrl:'',
					name:'王五',
					message:'隔壁老王',
					Date:'2022-7-9'
					
				},
				{
					imageUrl:'',
					name:'老六',
					message:'TC',
					Date:'2022-11-5'
					
				},
				{
					imageUrl:'',
					name:'老六',
					message:'TB',
					Date:'2022-11-5'
					
				},
				{
					imageUrl:'',
					name:'李四',
					message:'倒霉李四',
					Date:'2022-8-1'
					
				},,
				{
					imageUrl:'',
					name:'李四',
					message:'倒霉李四',
					Date:'2022-8-1'
					
				},
		
			]
		};
	},
	onLoad() {
		let _this=this
		uni.getSystemInfo({
			success(res) {
				_this.windowHeight=res.windowHeight;
				_this.view1=Math.floor(res.windowHeight*0.15);
				_this.view2=Math.floor(res.windowHeight*0.72);
			}
		})
	},
	methods:{
		goto(){
			uni.navigateTo({
				url:'/subpages/chat/chat'
			})
		}
	}
};
</script>

<style lang="scss">
page {
}

.flex-c {
	display: flex;
	flex-direction: column;
	justify-content: space-between;
}
.flex-row{
	display: flex;
	align-items: center;
	justify-content: space-between;
}
.outer{
	box-sizing: border-box;
	.box1{
	     padding: 20rpx 40rpx;
		 display: flex;
		 justify-content: space-between;
		 border-top: 1rpx solid #f5f3f2;
		 border-bottom: 1rpx solid #f5f3f2;
		
	}
	.scroll-view-content{
		white-space: nowrap;
		
		.dataList {
		   display: inline-block;
           width: 50px;
		   height: 70px;
		   margin-right: 40rpx;
		   &>view{
			   align-items: center;
			   .list {
			   	display: flex;
			   	width: 100rpx;
			   	height: 100rpx;
			   	border-radius: 50rpx;
			   	background: #007AFF;
			   	image{
			   		height: 100%;
			   		width: 100%;
			   	}
		   }
		   
		   }
		 }
		
		
	}
	
			
	
	.massage_list{
		position: sticky;
		padding: 20rpx;
	    box-sizing: border-box;
		.message_box{
			box-sizing: content-box;
			height: 80px;
			margin: auto 0;
			margin-bottom: 20rpx;
			display: flex;
			justify-content: space-between;
			align-items: center;
			border-bottom: 1rpx solid #f5f3f2;
			.message-item-left{
				display: flex;
				align-items: center;
				.item-image{
					height: 100rpx;
					width: 100rpx;
					border-radius: 60rpx;;
					background-color: white;
					image{
						height: 100%;
						width: 100%;
					}
				}
				.item-name{
					padding: 10rpx 0;
					margin-left: 20rpx;
					display: flex;
					flex-direction: column;
				    justify-content: space-between;
					
					.name{
						color: #272727;
						font-size: 20px;
					}
					.message{
						color: #959595;
					}
				}
			}
		    .message-item-right{
				height: 20px;
				width: fit-content;
				display: flex;
			
			}
		}
	} 
	
	
}
</style>
