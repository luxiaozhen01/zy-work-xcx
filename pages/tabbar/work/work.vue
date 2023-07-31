<template>
	<view>
		<view class="container">
			<view class="topTitleBox">
				<text class="title">早上好！张三先生</text>
				<view class='right'>
					<u-icon class="icon" color="#88bf01" size="28" name="bell"></u-icon>
					<view class="box">{{num}}</view>
				</view>
			</view>
			<view class="mian">
				<view class="swiper_container">
						  <u-swiper
								:list="list"
								@change="e => current = e.current"
								:autoplay="true"
								:circular="true"
								:radius='0'
							>
						    <view slot="indicator" class="indicator">
								<view
									 class="indicator__dot"
									 v-for="(item, index) in list"
									 :key="index"
									 :class="[index === current && 'indicator__dot--active']"
									 >
								</view>
							</view>
						</u-swiper>
					</view>
					<view class="centerContainer">
						<view class="centerItem">
							<view class="imgBox">
								<image src="/static/work/centerBox/huodong.png"></image>
							</view>
							<text>功能1</text>
						</view>
						<view class="centerItem">
							<view class="imgBox">
								<image src="/static/work/centerBox//fangkeyaoqing.png"></image>
							</view>
							<text>功能2</text>
						</view>
						<view class="centerItem">
							<view class="imgBox">
								<image src="/static/work/centerBox//jishiben.png"></image>
							</view>
							<text>功能3</text>
						</view>
						<view class="centerItem">
							<view class="imgBox">
								<image src="/static/work/centerBox//linliquan.png"></image>
							</view>
							<text>功能4</text>
						</view>
						<view class="centerItem">
							<view class="imgBox">
								<image src="/static/work/centerBox//zhuangxiushenqing.png"></image>
							</view>
							<text>功能5</text>
						</view>
					</view>
					<menu-list :list='bottomList' :state='0' @showPopup="showPopup"></menu-list>
				</view>
				<view class="popupContainer">
					<u-popup :show="show" mode="center"  @close="close"  :closeOnClickOverlay="true" :round="15">
						<view class="centent">
							<view class="top">{{popupTitle}}</view>
							<view class="bottom">
								<menu-list :list='popupList' :state='1'></menu-list>
							</view>
						</view>
					</u-popup>
				</view>
			</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				current:0,
				show:false,
				popupTitle:'',
				num:77,
				list: [
				    'https://cdn.uviewui.com/uview/swiper/swiper3.png',
				    'https://cdn.uviewui.com/uview/swiper/swiper2.png',
				    'https://cdn.uviewui.com/uview/swiper/swiper1.png',
				],
				bottomList:[
					{	
						title:'功能A',
						img:'/static/work/bottomBox/1.png'
					},{
						title:'功能B',
						img:'/static/work/bottomBox/2.png'
					},{
						title:'功能C',
						img:'/static/work/bottomBox/3.png'
					},{
						title:'功能D',
						img:'/static/work/bottomBox/4.png'
					},{
						title:'功能E',
						img:'/static/work/bottomBox/5.png'
					},{
						title:'功能F',
						img:'/static/work/bottomBox/6.png'
					},{
						title:'功能G',
						img:'/static/work/bottomBox/7.png'
					},{
						title:'功能H',
						img:'/static/work/bottomBox/8.png'
					},{
						title:'功能I',
						img:'/static/work/bottomBox/9.png'
					},{
						title:'功能J',
						img:'/static/work/bottomBox/10.png'
					},
				],
				popupList:[
					{
						title:'功能1',
						img:'/static/work/popup/1.png'
					},{
						title:'功能2',
						img:'/static/work/popup/2.png'
					},{
						title:'功能3',
						img:'/static/work/popup/3.png'
					},{
						title:'功能4',
						img:'/static/work/popup/4.png'
					},{
						title:'功能5',
						img:'/static/work/popup/5.png'
					},{
						title:'功能6',
						img:'/static/work/popup/6.png'
					},{
						title:'功能7',
						img:'/static/work/popup/7.png'
					},{
						title:'功能8',
						img:'/static/work/popup/8.png'
					},{
						title:'功能9',
						img:'/static/work/popup/9.png'
					},{
						title:'功能10',
						img:'/static/work/popup/10.png'
					},
				]
			};
		},
		methods:{
			showPopup(title){
				this.popupTitle = title
				this.show = true
			},
			close(){
				this.show = false
			}
		}
	}
</script>

<style lang="scss" scoped>
	.container{
		width: 100%;
		height: 88vh;
		background-color: #f1f1f1;
		.topTitleBox{
			width: 100%;
			line-height: 70rpx;
			background-color: #272a3b;
			color: #88bf01;
			padding-top: 70rpx;
			display: flex;
			justify-content: center;
			position: relative;
			
			.right{
				width: 60rpx;
				height: 60rpx;
				position: absolute;
				right: 15rpx;
				//#ifdef  MP-WEIXIN
					left: 15rpx;
				// #endif		
		
				.box{
					width: 30rpx;
					line-height: 30rpx;
					background-color:red; 
					border-radius: 15rpx 15rpx;
					position: absolute;
					top: 0rpx;
					left: 35rpx;
					text-align: center;
					font-size: 20rpx;
					color: #fff;
				}
			}
		}
		.mian{
			.swiper_container{
						.indicator {
							   @include flex(row);
							   justify-content: center;
								
							   &__dot {
									height: 8px;
									width: 8px;
									border: 1px solid #88bf01;
									border-radius: 100px;
									background-color: rgba(255, 255, 255, 0.35);
									margin: 0 5px;
									transition: background-color 0.3s;
						   
								   &--active {
										background-color: #88bf01;
									}
							   }
						   }
					}
				.centerContainer{
					width: 100%;
					height: 140rpx;
					display: flex;
					
					.centerItem{
							height: 100%;
							flex: 1;
							background-color:  #272a3b;
							font-size: 22rpx;
							display: flex;
							flex-direction: column;
							align-items: center;
							justify-content: center;
							color:#6c6d72;
							.imgBox{
								width: 80rpx;
								height: 80rpx;
								image{
									width: 100%;
									height: 100%;
								}
							}
						
					}
				}
				
			}
			.popupContainer{
				.centent{			
					width: 600rpx;
					height: 600rpx;
					border-radius: 10rpx 10rpx;
					.top{
						width: 100%;
						line-height:90rpx;
						border-top-left-radius: 10px 10px;
						border-top-right-radius: 10px 10px;
						color: #88bf01;
						background-color: #272a3b;
						text-align: center;
					}
					.bottom{
						background-color: #ffff;
						border-bottom-left-radius: 10px 10px;
						border-bottom-right-radius: 10px 10px;
					}
				}
		}
		
	}
</style>
