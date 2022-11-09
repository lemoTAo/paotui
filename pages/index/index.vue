<template>
    <view class="flex-col indexpage" :style="{height:windowHeight+'px'}">
        <view class="flex-col wrapper">
            <text class="select-service">
                选择服务
            </text>
            <view class="flex-row wraper-row" >
                <view class="box"   :class="[Page.service_active===1?'box_shadow':'']" @click="changeService_active(1)">
					<image src="../../static/index/order.png" mode=""></image>
				</view>
                <view class="box"   :class="[Page.service_active===2?'box_shadow':'']" @click="changeService_active(2)">
					<image src="../../static/index/runing.png" mode=""></image>
				</view>
            </view>
				<view class="flex-row wraper-row-two">
				    <text class="place-an-order">
				        下单
				    </text> 
					<text class="running-errands">
				        跑腿
				    </text>
				</view>
			
        </view>
        <view class="wraper-col wrapper-two">
			<text class="select-two">选择类型</text>
           <view class="flex-bw">
			   	 <view class="wraper-col" style="background-color: #e1f0f7" @click="changeTypeactive(1)" :class="[Page.type_active===1?'box_shadow':'']">
			   	 	<image src="../../static/index/packages.png" ></image>
			   	 	<text>快递</text>
					<view class="gou" v-show="Page.type_active==1" >
						<image src="../../static/index/gou.png"></image>
					</view>
			   	 </view>
			   	<view class="wraper-col flex-col " 
				  style="background-color: #f9f2de;"
				   :class="[Page.type_active===2?'box_shadow':'']"
				  @click="changeTypeactive(2)">
			   		<image src="../../static/index/food.png" ></image>
			   		<text>外卖</text>
					<view class="gou" v-show="Page.type_active==2">
						<image src="../../static/index/gou.png"></image>
					</view>
			   	</view>
		   </view>
        </view>
       <button class="button" @click="goto">下一步</button>
    </view>
</template>
<script>
    export default {
        data() {
            return {
				windowHeight:0,
				Page:{
					type_active:1,
					service_active:1,
				}

			}
        },
        methods: {
        },
		onLoad() {
			let _this=this
			uni.getSystemInfo({
				success(res) {
					_this.windowHeight=res.windowHeight
				}
			})
		},
		methods:{
			changeService_active(e){
				this.Page.service_active=e
			},
			changeTypeactive(e){
				this.Page.type_active=e
			},
			goto(){
				if(this.Page.service_active==1)
				uni.navigateTo({
					url:`/subpages/logistics1/logistics1?serive=${this.Page.service_active}&type=${this.Page.type_active}`
				})
				else if(this.Page.service_active==2)
				uni.navigateTo({
						url:`/subpages/order_receiving/order_receiving?serive=${this.Page.service_active}&type=${this.Page.type_active}`
				})
			}
		}
    }
</script>
<style lang="scss">


page {
        margin: 0;
        width: 100%;
        font-size: 16px;
		background-color: #ffffff;
}
    view,
    text,
    image {
        position: relative;
        box-sizing: border-box;
        flex-shrink: 0;
    }

    .flex-col {
        display: flex;
        align-items: flex-start;
        flex-direction: column;
    }

    .flex-row {
        display: flex;
        align-items: flex-start;
    }

    .flex-col .flex-row {
        width: 100%
    }
	.flex-bw{
		 display: flex;
		 justify-content: space-between;
	}
    .box_shadow{
		box-shadow: 10rpx 15rpx 6rpx #bfbfbf;
	}
    /** 全局样式-结束*/

    .indexpage {
        padding: 0rpx 48rpx ;

        .wrapper {
            width: 100%;
            height: 504rpx;
            margin: auto 0;

            .select-service {
				margin:auto 0;
                width: 144rpx;
                font-size: 36rpx;
                font-weight: 500;
            }

            .wraper-row {
                width: 654rpx;
                justify-content: space-between;
                margin-bottom: 24rpx;

                .box {
                    width: 280rpx;
                    height: 374rpx;
					border-radius: 20px;
					image{
						width: 100%;
						height: 100%;
					}
                }
            }

            .wraper-row-two {
                width: 444rpx;
                justify-content: space-between;
                margin-right: auto;
                margin-left: auto;

                .place-an-order {
                    font-size: 36rpx;
                    line-height: 28rpx; 
                }

                .running-errands {
                    width: 72rpx;
                    font-size: 34rpx;
                    line-height: 28rpx;
                }
            }

            
        }

        .wrapper-two {
			
            width: 654rpx;
            justify-content: space-between;
			margin: auto 0;
            padding: 0rpx 10rpx 0rpx 0rpx;
            border-radius: 20rpx;
			.select-two {
				   margin:auto 0;
				   width: 144rpx;
				   font-size: 36rpx;
				   font-weight: 500;
			}
            .wraper-col {
				position: relative;
				display: flex;
				flex-direction: column;
				justify-content: space-between;
                width: 278rpx;
                height: 276rpx;
				margin-top: 20rpx;
                border-radius: 20rpx;
				padding: 40rpx 40rpx;
					image{
						width: 50%;
						height: 50%;
					}
				.gou{
					position: absolute;
					top: 30rpx;
					right: 30rpx;
					width: 30rpx;
					height: 30rpx;
					cursor: pointer;
					image{
						width: 100%;
						height: 100%;
					}
				}	
            }
        }

        .button {
			height: 100rpx;
            width: 454rpx;
			line-height: 100rpx;
            display: block;
            margin: auto auto;
			border-radius: 150rpx;
			background-color:#655cf3 ;
        }
    }
</style>