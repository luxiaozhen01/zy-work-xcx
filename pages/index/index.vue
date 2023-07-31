<template>
	<view class="container">
		<view class="top">
			<template v-if="current == 0">
				<work></work>
			</template>
			<template v-if="current == 1">
				<helper></helper>
			</template>
			<template v-if="current == 2">
				<usual></usual>
			</template>
			<template v-if="current == 3">
				<analyse></analyse>
			</template>
			<template v-if="current == 4">
				<user></user>
			</template>
		</view>
		<view class="bottom">
			<my-tabBar :current-page="current" @clickTabBar="clicktabBar"></my-tabBar>
		</view>
	</view>
</template>

<script>
	import work from "@/pages/tabbar/work/work.vue"
	import helper from "@/pages/tabbar/helper/helper.vue"
	import usual from "@/pages/tabbar/usual/usual.vue"
	import analyse from "@/pages/tabbar/analyse/analyse.vue"
	import user from "@/pages/tabbar/user/user.vue"
	export default {
		components:{
			work,
			helper,
			usual,
			analyse,
			user
		},
		data() {
			return {
				current:0
			};
		},
		methods:{
			clicktabBar(num){
				this.current = num 
			}
		}
	}
</script>

<style lang="scss" scoped>
	.container{
		width: 100%;
		height: 100vh;
		background-color: #f1f1f1;
		.top{
			width: 100%;
			height: 88vh;
			overflow: auto;
		}
		.bottom{
			width: 100%;
			height: 12vh;
			position: fixed;
			bottom: 0;
			background-color: #fff;
		}
	}
</style>
