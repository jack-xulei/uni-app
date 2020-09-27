<template>
	<view class="container">
		<!-- 订单 -->
		<view class="order-section">
			<view class="order-item"  hover-class="common-hover"  :hover-stay-time="50"  @click="notDone">
				<text class="yticon icon-message1"></text>
				<text>服务通知</text>
			</view>
			<view class="order-item"  hover-class="common-hover" :hover-stay-time="50"  @click="notDone">
				<text class="yticon icon-message2"></text>
				<text>物流消息</text>
			</view>
			<view class="order-item"  hover-class="common-hover"  :hover-stay-time="50"  @click="notDone">
				<text class="yticon icon-message3"></text>
				<text>未读消息</text>
			</view>
		</view>
		<image :src="message" mode="" class="home-image" @click="notDone"></image>
	</view>
</template>

<script>
	import message from '@/static/images/message.png'
	export default {
		data() {
			return {
				message
			}
		},
		methods: {
			notDone() {
				uni.showToast({
				    title: '功能暂未开发',
				    icon: 'none'
				});
			}
		}
	}
</script>

<style scoped lang="scss">
	%section {
	  display:flex;
	  justify-content: space-around;
	  align-content: center;
	  background: #fff;
	  border-radius: 10upx;
	}
	%flex-center {
	 display:flex;
	 flex-direction: column;
	 justify-content: center;
	 align-items: center;
	}
	.order-section{
		@extend %section;
		padding: 28upx 0;
		margin-top: 20upx;
		.order-item{
			@extend %flex-center;
			width: 120upx;
			height: 120upx;
			border-radius: 10upx;
			font-size: 24upx;
			color: #303133;
		}
		.yticon{
			font-size: 48upx;
			margin-bottom: 18upx;
			color: #fa436a;
		}
		.icon-shouhoutuikuan{
			font-size:44upx;
		}
	}
	.icon-message1:before{
		content: "\e626";
	}
	.icon-message2:before{
		content: "\e614";
	}
	.icon-message3:before{
		content: "\e612";
	}
	.home-image {
		width: 100%;
		height: 630px;
	}
</style>
