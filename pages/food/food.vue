<template>
	<view class="foodMain">
		<block v-for="(item,index) in foodlist" :key="index">
			<view class="foodWrap">  
				<image class="foodPic" :src='item.pic'></image>
				<view class="foodName">{{item.name}}</view>
			</view>
		</block>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				foodlist:[{name:'手撕羊肉',pic:'/static/shousiyangrou.png'},
						  {name:'手撕猪肉',pic:'/static/shousiyangrou.png'},
						  {name:'手撕牛肉',pic:'/static/shousiyangrou.png'},
						  {name:'手撕羊肉',pic:'/static/shousiyangrou.png'},
						  {name:'手撕猪肉',pic:'/static/shousiyangrou.png'},
						  {name:'手撕牛肉',pic:'/static/shousiyangrou.png'},
						  {name:'手撕羊肉',pic:'/static/shousiyangrou.png'},
						  {name:'手撕猪肉',pic:'/static/shousiyangrou.png'},
						  {name:'手撕牛肉',pic:'/static/shousiyangrou.png'},
						  {name:'手撕驴肉',pic:'/static/shousiyangrou.png'},
						],
					}
		},
		methods: {
			
		}
	}
</script>

<style lang="scss">
	.foodMain{
		width: 100%;
		height: 100%;
		position: fixed;
		padding:0% 2%;
		box-sizing: border-box;
		background: #f7f7f7;
		
		.foodWrap{
			display: inline-block;
			width: 46%;
			height: 15.6%;
			margin: 2%;
			box-sizing: border-box;
			background: white;
			text-align: center;
			
			.foodPic{
				width: 83%;
				height: 70%;
				margin:7% 1% 0% 1%;
				box-sizing: border-box;
			}
			
			.foodName{
				font-size:16rpx;
				font-family:SimHei;
				color:rgba(51,51,51,1);
				line-height:18rpx;
				margin-top: 10rpx;
			}
		}
		
	}

</style>
