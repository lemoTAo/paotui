<template>
	<view class="outer .flex_c" :style="{height:windowHeight+'px'}">
		<!-- <van-transition name="fade-dowb" v-if="!show"> -->
			<view class="express_info flex_c" :style="{height:view1+'px'}">
				<view class="userInfo .flex_c">
					<text>凉拌嘻嘻</text>
					<text>学号：123456</text>
				</view>
				<view class="express-detail-info .flex_r_st">
					<view class="right-item .flex_c_ce">
						<image src="../../static/order/packages.png" mode=""></image>
					</view>
					<view class="left-item flex_c">
						<text>￥9</text>
						<text>快递代取</text>
						<text>C4快递超市</text>
					</view>
				</view>
			</view>
		<!-- </van-transition>s -->
		<!-- <view class="chat-box flex_c_st">
			<view class="chat-item flex_r_st " v-for="message,index in chat"  :key="index" :class="[message.id==2?'row_reverse':'']" >
				<view class="touxiang">
					<image src="/static/chat/IMG_-1.png" mode=""></image>
				</view>
				<view class="chat-message ">
					<text class="text">{{message.message}}</text>
				</view>
			</view>
			
		</view> -->
		<scroll-view scroll-y="true"  :style="{height:view2+'px'}" :scroll-top="top">
			<view class="chat-box flex_c_st">
				<van-transition name="fade-up">
					<view class="chat-item flex_r_st "
					v-for="message,index in chat"  
					:key="index" 
					:class="[message.id==2?'row_reverse':'']" >
						<view class="touxiang">
							<image src="/static/chat/IMG_-1.png" mode=""></image>
						</view>
						<view class="chat-message ">
							<text class="text">{{message.message}}</text>
						</view>
					</view>
				</van-transition>
				
			</view>
			
		</scroll-view>
		<view class="send-box .flex_r_st">
			<input type="text" style="background-color: antiquewhite;" 
			@input="getFocus($event)" 
			v-model="value"
             class="input"> 
			<van-transition  name="fade-right" v-if="show">
			 <button  class="btn" @click="sendmessage">发送</button>
			</van-transition>
			
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				windowHeight:0,
				view1:0,
				view2:0,
				show:false,//发送隐藏
				value:'',//
				top:0,//聊天高度
				// 模拟数据
				chat:[{
				id:1,	
				message:'hello，给钱'
				},
				{
				id:2,	
				message:'hello，没钱'
				},
				{
				id:1,	
				message:'hello，p'
				}
]
			};
		},
		methods:{
			getFocus(e){
				
					 // let height = e.detail.height  
				console.log(e.detail.value)
				if(e.detail.value.trim()){
					this.show=true  
				}
				else
				this.show=false
			},
			sendmessage(){
				if(!this.value)
				return ''
				let obj={id:2,message:this.value}
				this.value=''
				this.chat.push(obj)
				this.getChatBoxTop()
			},
			getChatBoxTop(){
				let _this=this
				let top=uni.createSelectorQuery().select('.chat-box')
				top.boundingClientRect(data=>{
					console.log(Math.floor(data.height))
					_this.top=Math.floor(data.height)
				}).exec()
			}
		},
		onLoad() {
			let _this=this
			uni.getSystemInfo({
				success:res=> {
					_this.windowHeight=res.windowHeight;
					_this.view1=Math.floor(res.windowHeight*0.15);
					_this.view2=Math.floor(res.windowHeight*0.7);
				}
			})
			this.getChatBoxTop()
		},
		onReady() {
			
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
	.flex_c_st{
		display: flex;
		justify-content: flex-start;
		flex-direction: column;
	}
	.flex_r{
		display: flex;
		justify-content: space-between;
	}
	.flex_r_st{
		display: flex;
		justify-content: flex-start;
	}
	.row_reverse{
	            flex-direction: row-reverse!important;
		&> .chat-message{
		    margin-left: 0 !important;
			margin-right: 20px;
		 	align-items: center;
		 	padding: 10px ;
		 	width: fit-content;
		 	max-width: 100rpx;
		 	color: white!important;
		 	background-color: #675ef5!important;
			box-shadow: none !important;
		 	.text{
		 	flex:1;
		 	overflow:hidden;
		 	word-wrap:break-word;
		 	word-break:break-all;
		 	font-size:12px;
		 	display:flex;
		 		
		   }

		}		
    };

	.outer{
		color: white;
		.express_info{
			position: sticky;
			height: 220rpx;
			padding: 10px 30rpx;
			background-color: #675ef5;
			overflow: hidden;
			.userInfo{
				&>text:nth-child(1){
					font-size: 36rpx;
					font-weight: 800;
				}
				&>text:nth-child(2){
					font-size: 24rpx;
				}
			}
			.express-detail-info{
				.right-item{
					width: 60px;
					height: 60px;
					margin-right: 10px;
					background-color: #eeeefa;
					border-radius: 10px;
					image{
						width: 70%;
						height: 70%;
					}
				}
				.left-item{
					font-size: 24rpx;
					&>text:nth-child(1){
						font-size: 28rpx;
						font-weight: 800;
					}
				}
			}
		}
	     .chat-box{
			 padding: 20px 30rpx;
			 overflow: hidden;
			 .chat-item{
				 margin-top: 10px;
				 position: relative;
				 // align-items: center;
				 .touxiang{
					
					 height: 45px;
					 width: 45px;
					 image{
						 height: 100%;
						 width: 100%;
					 }
				 }
				 .chat-message{
					 display: flex;
					 align-items: center;
					 justify-content: center;
					 margin-left: 20px;
					 padding: 10px ;
					 height: 100%;
					 width: fit-content;
					 max-width: 300rpx;
					 color: black;
					 border-radius: 10px;
					 background-color: white;
					 box-shadow: 10rpx 10rpx 2px #eaeef3;
					 .text{
						letter-spacing: 1px;
						overflow:hidden;
						word-wrap:break-word;
						word-break:break-all;
						font-size:14px;
						line-height: 150%;
					 }
				 }
			 }
		 }
	     .send-box{
			 color: black;
			 padding-top: 10rpx;
			 padding-left: 50px;
			 margin-bottom: 10px;
			 height: 60rpx;
			 border-top: 1px solid #e5e5e5;
			 .input{
				 height: 100%;
				 margin-right: 10rpx;
				 padding: 10rpx 40rpx;
				 width: 80%;
				 border-radius:10px ;
				 box-sizing: border-box;
			 }
			 .btn{
				 height: 100%;
				 font-size: 26rpx;
				 padding: 10rpx 20rpx;
				 line-height: 40rpx;
				 border-radius: 10rpx;
				 background-color: darkseagreen;
				 box-sizing: border-box;
			 }
		 }
	}
</style>
