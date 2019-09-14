<template>
	<view class="content">
		<mapWrap></mapWrap>
		<view class="foodStyleWrap">
			<view class="foodStyleTitle">中华八大菜系</view>
			<view class="foodStyleList">
				<block v-for="(item,index,) in foodstylelist" :key="index">
					<view class="foodStyle">{{item}}</view>
				</block>
			</view>
		</view>
	</view>
</template>

<script>
	import mapWrap from '@/components/map/mapWrap.vue';
	export default {
		components: {
			mapWrap
		},
		data() {
			return {
				foodstylelist:['川菜','徽菜','鲁菜','闽菜','苏菜','湘菜','粤菜','浙菜']
			}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style lang="scss">
	.content {
		width: 100%;
		height: 100%;
		position: fixed;
		background: #f7f7f7;
		
		.foodStyleWrap{
			display: flex;
			flex-direction: column;
			align-items: center;
			width: 100%;
			margin-top: 10%;
			
			.foodStyleTitle{
				width: 100%;
				font-size: 40rpx;
				color: black;
				text-align: center;
			}
			
			.foodStyleList{
				width: 90%;
				text-align: center;
				margin-top: 5%;
				
				.foodStyle{
					display: inline-block;
					width: 18%;
					height: 60rpx;
					font-size: 30rpx;
					line-height: 60rpx;
					color: black;
					background: white;
					text-align: center;
					margin:3% 3%;
				}
			}
		}
	}

</style>
