<template>
	<view class="content">
    <view class="title" hover-class="title-hover" @tap="changelang">
    	到{{currentlang}}
			<text class="iconfont icon-xiala"></text>
    </view>
		<textarea class="transformText" value="" placeholder="请输入您要翻译的文字" maxlength="140" @confirm="getText" @blur="getText">
			</textarea>
		<title>翻译后为</title>
		<view class="transformTextAfter">{{currentText}}</view>
	</view>
</template>

<script>
	const that = this 
	export default {
		data() {
			return {
				currentlang: 'xibanya',
				currentText: ''
			}
		},
		onLoad() {

		},
		methods: {
			changelang(e){
				uni.navigateTo({
					url:`/pages/change/change?currentlang=${this.currentlang}`,
					success: function(){
							
					},
					fail:function(){
						uni.showToast({
							title:'跳转失败，请重试',
							icon: 'none'
						})
					}
				})
			},
			getText(e){
				this.currentText = e.detail.value
			}
		}
	}
</script>
<style>
	@import url("../../static/mp-weixin/iconfont/iconfont.css");
</style>
<style scoped>
	.content {
		text-align: left;
		height: 400upx;
	}
	.title {
		font-size: 36upx;
		color: #8f8f94;
		border: 1px red solid;
		padding-left: 50upx;
		width: 654upx;
	}
	.transformText,.transformTextAfter{
		height: 400upx;
		width: 700upx;
		border: 1px black solid;
	}
	.title-hover{
		color: blue;
	}
	@keyframes rotate{
		from{
			transform: rotateZ(0deg);
			}
		to{
			transform: rotateZ(180deg);
			
			}
	}
	.title-hover>.icon-xiala{
		transform-origin: 50% 40%;
		display: inline-block;
		animation-duration: 0.5s;
		animation-name: rotate;
	}
</style>
