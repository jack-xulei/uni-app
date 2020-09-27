<template>
	<view class="container">
		<view class="list-cell b-b m-t" @click="navTo('个人资料')" hover-class="cell-hover" :hover-stay-time="50">
			<text class="cell-tit">个人资料</text>
			<text class="cell-more yticon icon-you"></text>
		</view>
		<view class="list-cell b-b" @click="navTo('收货地址')" hover-class="cell-hover" :hover-stay-time="50">
			<text class="cell-tit">公司信息</text>
			<text class="cell-more yticon icon-you"></text>
		</view>
		<view class="list-cell" @click="navTo('实名认证')" hover-class="cell-hover" :hover-stay-time="50">
			<text class="cell-tit">实名认证</text>
			<text class="cell-more yticon icon-you"></text>
		</view>
		
		<view class="list-cell m-t">
			<text class="cell-tit">消息推送</text>
			<switch checked color="#FB3633" @change="switchChange" />
		</view>
		<view class="list-cell m-t b-b" @click="navTo('清除缓存')" hover-class="cell-hover" :hover-stay-time="50">
			<text class="cell-tit">清除缓存</text>
			<text class="cell-more yticon icon-you"></text>
		</view>
		<view class="list-cell b-b" @click="navTo('关于Dcloud')" hover-class="cell-hover" :hover-stay-time="50">
			<text class="cell-tit">关于鼎捷</text>
			<text class="cell-more yticon icon-you"></text>
		</view>
		<view class="list-cell">
			<text class="cell-tit">检查更新</text>
			<text class="cell-tip">当前版本 1.0.0</text>
			<text class="cell-more yticon icon-you"></text>
		</view>
		<view class="list-cell log-out-btn" @click="toLogout">
			<text class="cell-tit">退出登录</text>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			};
		},
		methods:{

			navTo(url){
			},
			//退出登录
			toLogout(){
				uni.showModal({
				    content: '确定要退出登录么',
				    success: (e)=>{
				    	if(e.confirm){
				    		setTimeout(()=>{
				    			uni.navigateBack();
				    		}, 200)
				    	}
				    }
				});
			},
			//switch
			switchChange(e){
				let statusTip = e.detail.value ? '打开': '关闭';
				uni.showToast({
				    title: `${statusTip}消息推送`,
				    icon: 'none'
				});
			},

		}
	}
</script>

<style lang='scss'>
	.icon-you:before {
	    content: "\e606";
	}
	
	page{
		background: #f8f8f8;
	}
	.list-cell{
		display:flex;
		align-items:baseline;
		padding: 20upx 30upx;;
		line-height:60upx;
		position:relative;
		background: #fff;
		justify-content: center;
		&.log-out-btn{
			margin-top: 40upx;
			.cell-tit{
				color: #FB3633;
				text-align: center;
				margin-right: 0;
			}
		}
		&.cell-hover{
			background:#fafafa;
		}
		&.b-b:after{
			left: 30upx;
		}
		&.m-t{
			margin-top: 16upx; 
		}
		.cell-more{
			align-self: baseline;
			font-size: 32upx;
			color:  #909399;
			margin-left:10upx;
		}
		.cell-tit{
			flex: 1;
			font-size: 28upx + 2upx;
			color: #303133;
			margin-right:10upx;
		}
		.cell-tip{
			font-size: 28upx;
			color:  #909399;
		}
		switch{
			transform: translateX(16upx) scale(.84);
		}
	}
	.b-b:after, .b-t:after {
	    position: absolute;
	    z-index: 3;
	    left: 0;
	    right: 0;
	    height: 0;
	    content: '';
	    -webkit-transform: scaleY(0.5);
	    transform: scaleY(0.5);
	    border-bottom: 1px solid #E4E7ED;
		bottom: 0;
	}
</style>
