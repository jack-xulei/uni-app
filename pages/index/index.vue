<template>
	<view class="container">
		 <swiper class="swiper" :indicator-dots="true" :autoplay="true" :interval="2000" :duration="500">
			<swiper-item v-for="(banner, index) in banners" :key="index">
				<view class="swiper-item">
					<image :src="banner" class="swiper-image"></image>
				</view>
			</swiper-item>
		</swiper>
		<image :src="home" mode="" class="home-image" @click="notDone"></image>
	</view>
</template>

<script>
	import banner1 from '@/static/images/banner/banner1.png'
	import banner2 from '@/static/images/banner/banner2.png'
	import banner3 from '@/static/images/banner/banner3.png'
	import home from '@/static/images/home.png'
	export default {
		data() {
			return {
				banners: [banner1, banner2,	banner3],
				home
			}
		},
		methods: {
			notDone() {
				uni.showToast({
				    title: '功能暂未开发',
				    icon: 'none'
				});
			},
			//点击导航栏 buttons 时触发
			onNavigationBarButtonTap(e) {
				const index = e.index;
				if (index === 0) {
					uni.scanCode({
					    scanType: ['barCode'],
					    success: function (res) {
					        console.log('条码类型：' + res.scanType);
					        console.log('条码内容：' + res.result);
					    }
					});
				}else {
					this.notDone()
				}
			}
		}
	}
</script>

<style scoped lang="scss">
	.swiper{
		// margin-top: 100rpx;
	}
	.swiper-image{
		padding: 0;
		width: 100%;
	}
	.home-image {
		width: 100%;
		height: 440px;
	}
</style>
