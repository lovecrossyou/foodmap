<template>
	<view class="content">
		<view class="">
			<areaMap></areaMap>
		</view>
		<Star></Star>
	</view>
</template>

<script>
	import areaMap from '@/components/area-map.vue'
	import Star from '@/components/my-star.vue'
	export default {
		components: {
			areaMap,
			Star
		},
		data() {
			return {
				title: 'Hello'
			}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style>
	.content {
		/* display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center; */
	}

	.logo {
		height: 200upx;
		width: 200upx;
		margin-top: 200upx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50upx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36upx;
		color: #8f8f94;
	}
</style>
