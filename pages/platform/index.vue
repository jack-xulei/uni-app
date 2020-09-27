<template>
	<view class="container">
		<image :src="banner1" mode="" class="platform-image"></image>
		<view class="main d-d">
			<view class="customer">
				<image :src="onePersion" mode="" class="customer-image"></image>
				<text class="cell-tit">我是客户</text>
			</view>
			<text class="cell-more yticon icon-you" @click="openCustomer('http://192.168.9.157:9020/')">进入我的供应商平台</text>
		</view>
		<view class="main">
			<view class="customer">
				<image :src="morePersion" mode="" class="customer-image"></image>
				<text class="cell-tit">我是供应商</text>
			</view>
			<text class="cell-more yticon icon-you" @click="notDone">更多</text>
		</view>
		<view class="order-section d-d">
			<view class="order-item"  hover-class="common-hover" :hover-stay-time="50"  @click="openCustomer()" v-for="item in 8" :key="item">
				<image :src="persion" mode="" class="icon-image"></image>
				<text>客户{{item}}</text>
			</view>
		</view>
		<view class="main">
			<view class="customer">
				<image :src="application" mode="" class="customer-image"></image>
				<text class="cell-tit">应用中心</text>
			</view>
			<text class="cell-more yticon icon-you" @click="notDone">更多</text>
		</view>
		<view class="order-section">
			<view class="order-item"  hover-class="common-hover" :hover-stay-time="50"  @click="openCustomer(item.url)" v-for="(item, index) in appList" :key="index">
				<image :src="item.icon" mode="" class="icon-image"></image>
				<text>{{item.name}}</text>
			</view>
		</view>
	</view>
</template>

<script>
	import banner1 from '@/static/images/banner/banner1.png' 
	import onePersion from '@/static/images/platform/one-persion.png' 
	import morePersion from '@/static/images/platform/more-persion.png' 
	import persion from '@/static/images/persion.png' 
	import application from '@/static/images/application.png'
	import ticket from '@/static/images/platform/ticket.png'
	import cat from '@/static/images/platform/cat.png'
	import shop from '@/static/images/platform/shop.png'
	import plane from '@/static/images/platform/plane.png'
	import elec from '@/static/images/platform/elec.png'
	import location from '@/static/images/platform/location.png'
	import wms from '@/static/images/platform/wms.png'
	import deng from '@/static/images/platform/deng.png'
	export default {
		data() {
			return {
				banner1,
				onePersion,
				morePersion,
				persion,
				application,
				url: encodeURIComponent('http://newsrmwx.dev.zhilink.com'),
				myUrl: 'http://192.168.9.157:9020/',
				appList: [{
					icon: ticket,
					url: 'https://hellouniapp.dcloud.net.cn',
					name: '电子发票'
				}, {
					icon: elec,
					url: 'https://www.baidu.com/',
					name: '电子签章'
				}, {
					icon: cat,
					url: 'https://youzan.github.io/vant/#/zh-CN/',
					name: '无车承运'
				}, {
					icon: location,
					url: 'http://newsrmwx.dev.zhilink.com',
					name: '物流追踪'
				}, {
					icon: shop,
					url: 'http://newsrmwx.dev.zhilink.com',
					name: '物资超市'
				},
				{
					icon: deng,
					url: 'http://newsrmwx.dev.zhilink.com',
					name: '工艺市场'
				},
				{
					icon: plane,
					url: 'http://newsrmwx.dev.zhilink.com',
					name: '空运渠道'
				},
				{
					icon: wms,
					url: 'http://newsrmwx.dev.zhilink.com',
					name: '智联云仓'
				}]
			}
		},
		methods: {
			openCustomer(url = this.url) {
				uni.navigateTo({
				    url: `/pages/component/web-view?url=${url}`
				});
			},
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
	.container {
		background-color: #f8f8f8;
		margin-bottom: 20rpx;
	}
	.main{
		display: flex;
		justify-content: space-between;
		padding-left: 40rpx;
		padding-right: 40rpx;
		align-items: center;
		background-color: #FFFFFF;
		.cell-more{
			font-size: 24upx;
			color:  #909399;
			margin-left:10upx;
		}
		.icon-you:after {
		    content: "\e606";
		}
		.cell-tit{
			color: #303133;
			font-size: 30rpx;
		}
	}
	.d-d {
		margin-bottom: 20rpx;
	}
	.platform-image {
		width: 100%;
		height: 150px;
	}
	.customer {
		height: 100rpx;
		line-height: 100rpx;
		display: flex;
		align-items: center;
		.customer-image{
			width: 40rpx;
			height: 40rpx;
			margin-right: 20rpx;
		}
	}
	.icon-image{
		width: 48rpx;
		height: 48rpx;
		margin-bottom: 20rpx;
	}
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
		padding: 0rpx 100rpx;
		display: flex;
		flex-wrap: wrap;
		.order-item{
			@extend %flex-center;
			width: 25%;
			height: 140upx;
			border-radius: 10upx;
			font-size: 24upx;
			color: #303133;
		}
		.yticon{
			font-size: 24upx;
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
</style>
