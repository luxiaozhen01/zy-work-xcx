<template>
	<view>
		<view :class="[state==0 ? 'bottomContainer' : 'popupList']">
			<view :class="[state==0 ? 'bottomItem' : 'popupItem']" v-for="(item,index) in list" :key=index @click='clickItem(item,index)'>
				<view :class="[state==0 ? 'imgContainer' : 'popupImg']">
					<image :src="item.img"></image>
				</view>
				<text>{{item.title}}</text>
			</view>
			<view :class="[state==0 ? 'bottomItem' : 'popupItem']"></view>
			<view :class="[state==0 ? 'bottomItem' : 'popupItem']"></view>
		</view>
	</view>
</template>

<script>
	export default {
		name:"menu-list",
		props:{
			list:{
				type:Array,
				default:()=>[]
			},
			state:{
				type:Number,
				default:0
			}
		},
		data() {
			return {
				
			};
		},
		methods:{
			clickItem(item,index){
				if(index == 1){
					this.$emit("showPopup",item.title)
				}
			}
		}
	}
</script>

<style lang="scss" scoped>
	.bottomContainer{
		width: 100%;
		height: 624rpx;
		box-sizing: border-box;
		border: 1px solid #e7e6e4;
		// background-color: red;
		margin-top: 8rpx;
		display: flex;
		flex-direction: row;
		flex-wrap: wrap;
		.bottomItem{
			box-sizing: border-box;
			width: 25%;
			height: 208rpx;
			border: 1px solid #e7e6e4;
			color:#6c6d72;
			display: flex;
			flex-direction: column;
			align-items: center;
			justify-content: center;
			.imgContainer{
				width: 140rpx;
				height: 140rpx;
				image{
					width: 100%;
					height: 100%;
				}
			}
		}
	}
	.popupList{
		width: 600rpx;
		height: 520rpx;
		// background-color: red;
		display: flex;
		flex-direction: row;
		flex-wrap: wrap;
		.popupItem{
			width: 150rpx;
			height: 170rpx;
			// background-color: blue;
			display: flex;
			flex-direction: column;
			align-items: center;
			justify-content: center;
			font-size: 26rpx;
			color:#6c6d72;
			.popupImg{
				width: 100rpx;
				height: 100rpx;
				image{
					width: 100%;
					height: 100%;
				}
			}
		}
	}
</style>