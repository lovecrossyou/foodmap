<template>
	<view class="qiun-columns">
		<view class="qiun-charts">
			<!--#ifdef MP-ALIPAY -->
			<canvas canvas-id="canvasWord" id="canvasWord" class="charts" :width="cWidth*pixelRatio" :height="cHeight*pixelRatio"
			 :style="{'width':cWidth+'px','height':cHeight+'px'}" @touchstart="touchWord"></canvas>
			<!--#endif-->
			<!--#ifndef MP-ALIPAY -->
			<canvas canvas-id="canvasWord" id="canvasWord" class="charts" @touchstart="touchWord"></canvas>
			<!--#endif-->
		</view>
	</view>
</template>

<script>
	import uCharts from '@/components/u-charts/u-charts.js';
	import {
		isJSON
	} from '@/common/checker.js';
	import dataJson from '@/common/data.json'

	var _self;
	var canvaWord = null;
	export default {
		data() {
			return {
				cWidth: '',
				cHeight: '',
				pixelRatio: 1,
				textarea: ''
			}
		},
		onLoad() {
			_self = this;
			//#ifdef MP-ALIPAY
			uni.getSystemInfo({
				success: function(res) {
					if (res.pixelRatio > 1) {
						//正常这里给2就行，如果pixelRatio=3性能会降低一点
						//_self.pixelRatio =res.pixelRatio;
						_self.pixelRatio = 2;
					}
				}
			});
			//#endif
			this.cWidth = uni.upx2px(750);
			this.cHeight = uni.upx2px(500);
			this.getServerData();
		},
		methods: {
			getServerData() {
				let Word = {
					series: []
				};
				Word.series = [{
					name: "跨全端图表",
					textSize: 25,
				}, {
					name: "微信小程序",
					textSize: 20,
				}, {
					name: "支付宝小程序",
					textSize: 20,
				}, {
					name: "百度小程序",
					textSize: 20,
				}, {
					name: "QQ小程序",
					textSize: 20,
				}, {
					name: "头条小程序",
					textSize: 20,
				}, {
					name: "抖音小程序",
					textSize: 20,
				}, {
					name: "360小程序",
					textSize: 20,
				}, {
					name: "跨全端",
					textSize: 10,
				}, {
					name: "跨全端",
					textSize: 12,
				}, {
					name: "跨全端",
					textSize: 10,
				}, {
					name: "跨全端",
					textSize: 12,
				}, {
					name: "跨全端",
					textSize: 10,
				}, {
					name: "跨全端",
					textSize: 12,
				}, {
					name: "跨全端",
					textSize: 10,
				}, {
					name: "跨全端",
					textSize: 12,
				}];
				_self.textarea = JSON.stringify(Word);
				_self.showWord("canvasWord", Word);
			},
			showWord(canvasId, chartData) {
				canvaWord = new uCharts({
					$this: _self,
					canvasId: canvasId,
					type: 'word',
					background: '#000000',
					animation: true,
					pixelRatio: _self.pixelRatio,
					series: chartData.series,
					width: _self.cWidth * _self.pixelRatio,
					height: _self.cHeight * _self.pixelRatio,
					extra: {
						word: {
							type: 'normal'
						}
					}
				});
			},
			touchWord(e) {
				canvaWord.showToolTip(e, {
					format: function(item) {
						return item.name
					}
				});
			},
			changeData() {
				if (isJSON(_self.textarea)) {
					let newdata = JSON.parse(_self.textarea);
					canvaWord.updateData({
						series: newdata.series
					});
				} else {
					uni.showToast({
						title: '数据格式错误',
						image: '../../../static/images/alert-warning.png'
					})
				}
			},
			saveImage() {
				uni.canvasToTempFilePath({
					canvasId: canvaWord.opts.canvasId,
					success: function(res) {
						//#ifdef H5
						console.log(res.tempFilePath)
						//#endif
						//#ifndef H5
						uni.saveImageToPhotosAlbum({
							filePath: res.tempFilePath,
							success: function() {
								uni.showToast({
									title: '保存成功',
									duration: 2000
								});
							}
						});
						//#endif
					}
				});
			}
		}
	}
</script>

<style>
	/*样式的width和height一定要与定义的cWidth和cHeight相对应*/
	.qiun-charts {
		width: 750upx;
		height: 500upx;
		background-color: #FFFFFF;
	}

	.charts {
		width: 750upx;
		height: 500upx;
		background-color: #FFFFFF;
		font-weight: ;
	}
</style>
