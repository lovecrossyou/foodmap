<template>
	<view class="content">
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
	export default {
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
		padding-top: 5%;
		background: #f7f7f7;
		
		.foodStyleWrap{
			display: flex;
			flex-direction: column;
			align-items: center;
			width: 100%;
			margin-top: 10%;
			box-sizing: border-box;
			
			.foodStyleTitle{
				width: 100%;
				font-size:16px;
				font-family:PingFangHK;
				font-weight:400;
				color:rgba(51,51,51,1);
				line-height:22rpx;
				text-align: center;
			}
			
			.foodStyleList{
				width: 98%;
				text-align: center;
				margin-top: 5%;
				
				.foodStyle{
					display: inline-block;
					width: 18%;
					height: 60rpx;
					font-size:14rpx;
					font-family:PingFangHK;
					font-weight:400;
					color:rgba(51,51,51,1);
					line-height:60rpx;
					background: white;
					text-align: center;
					margin:3% 3%;
					box-sizing: border-box;
				}
			}
		}
	}

</style>
