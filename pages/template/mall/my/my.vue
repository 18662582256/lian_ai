<template>
	<view class="container">
		<tui-list-view>
			<view class="tui-section-card">
				<image src="/static/images/mall/my/defaultavatar.png" class="g-image" />
				<view class="tui-btn-box" @click="toLoginPage">
					<tui-button>登录/注册</tui-button>
				</view>
			</view>
			<tui-list-cell @click="activation" :arrow="true">
				<view class="tui-item-box">
					<image src="/static/images/mall/my/vip.png" class="list-image" />
					<text class="tui-list-cell_name">自助激活</text>
				</view>
			</tui-list-cell>
			<tui-list-cell @click="detail" :arrow="true">
				<view class="tui-item-box">
					<image src="/static/images/mall/my/active.png" class="list-image" />
					<view class="tui-list-cell_name">激活码解锁</view>
				</view>
			</tui-list-cell>
			<tui-list-cell @click="detail" :arrow="true">
				<view class="tui-item-box">
					<image src="/static/images/mall/my/spread.png" class="list-image" />
					<view class="tui-list-cell_name">我要推广</view>
				</view>
			</tui-list-cell>
			<tui-list-cell @click="detail" :arrow="true">
				<view class="tui-item-box">
					<image src="/static/images/mall/my/ai.png" class="list-image" />
					<view class="tui-list-cell_name">AI导师</view>
				</view>
			</tui-list-cell>
			<tui-list-cell @click="detail" :arrow="true">
				<view class="tui-item-box">
					<image src="/static/images/mall/my/phone.png" class="list-image" />
					<view class="tui-list-cell_name">手机绑定</view>
				</view>
			</tui-list-cell>
			<tui-list-cell>
				<view class="tui-item-box">
					<image src="/static/images/mall/my/kefu.png" class="list-image" />
					<view class="tui-list-cell_name">联系客服</view>
					<view class="tui-ml-auto">
						<view class="tui-list-cell_name">
							<view class="tui-right">{{text}}</view>
							<view class="tui-right tui-right-btn" @tap="clipboard(text)">复制</view>
						</view>


					</view>
				</view>
			</tui-list-cell>
			<tui-list-cell @click="detail">
				<view class="tui-item-box">
					<image src="/static/images/mall/my/same.png" class="list-image" />
					<view class="tui-list-cell_name">我也想做一个话术程序</view>
				</view>
			</tui-list-cell>
			<tui-list-cell @click="detail" :arrow="true">
				<view class="tui-item-box">
					<image src="/static/images/mall/my/suggest.png" class="list-image" />
					<view class="tui-list-cell_name">投诉建议</view>
				</view>
			</tui-list-cell>
			<tui-list-cell @click="detail" last="true">
				<view class="tui-item-box">
					<image src="/static/images/mall/my/version.png" class="list-image" />
					<text class="tui-list-cell_name">当前版本</text>
					<view class="tui-right">1.87</view>
				</view>
			</tui-list-cell>
		</tui-list-view>
		<view class="tui-btn-service" @tap="back">
			<image src='/static/images/mall/kefu.png' class="tui-my-bg" mode="widthFix"></image>
		</view>
	</view>
</template>

<script>
	const thorui = require("@/components/common/tui-clipboard/tui-clipboard.js")
	export default {
		data() {
			return {
				text: "导师微信 93715665",
				isLogin:true
			}
		},
		methods: {
			detail: function() {
				this.tui.toast("click~")
			},
			// 登录注册
			toLoginPage:function(){
				uni.navigateTo({
					url: '../login/login'
				});
			},
			// 自助激活
			activation:function(){
				if(this.isLogin){
					uni.navigateTo({
						url: '../activation/activation'
					});
				}else{
					uni.navigateTo({
						url: '../login/login'
					});
				}
			},
			clipboard: function(event) {
				console.log("text", event);
				let data = event.split('')[1];
				thorui.getClipboardData(data, (res) => {
					// #ifdef H5 || MP-ALIPAY
					if (res) {
						this.tui.toast("复制成功")
					} else {
						this.tui.toast("复制失败")
					}
					// #endif
				}, event)
			}




		},


	}
</script>

<style>
	.tui-header-box {
		width: 100%;
		padding: 0 30rpx 0 20rpx;
		box-sizing: border-box;
		position: fixed;
		top: 0;
		left: 0;
		display: flex;
		align-items: center;
		justify-content: flex-end;
		height: 32px;
		transform: translateZ(0);
		z-index: 9999;
	}

	/* #ifndef MP */
	.tui-header-icon {
		min-width: 120rpx;
		display: flex;
		align-items: center;
		justify-content: space-between;
	}

	/* #endif */
	/* #ifdef MP */
	.tui-set-box {
		display: flex;
		align-items: center;
		justify-content: space-between;
	}

	/* #endif */
	.tui-icon-box {
		position: relative;
	}

	.tui-icon-setup {
		margin-left: 8rpx;
	}

	.tui-badge {
		position: absolute;
		font-size: 24rpx;
		height: 32rpx;
		min-width: 20rpx;
		padding: 0 6rpx;
		border-radius: 40rpx;
		right: 10rpx;
		top: -5rpx;
		transform: scale(0.8) translateX(60%);
		transform-origin: center center;
		display: flex;
		align-items: center;
		justify-content: center;
		z-index: 10;
	}

	.tui-badge-red {
		background: #F74D54;
		color: #fff;
	}

	.tui-badge-white {
		background: #fff;
		color: #F74D54;
	}

	.tui-badge-dot {
		position: absolute;
		height: 12rpx;
		width: 12rpx;
		border-radius: 50%;
		right: -12rpx;
		top: 0;
		background: #F74D54;
	}

	.tui-mybg-box {
		width: 100%;
		height: 464rpx;
		position: relative;
	}

	.tui-my-bg {
		width: 100%;
		height: 464rpx;
		display: block;
	}

	.tui-header-center {
		position: absolute;
		width: 100%;
		height: 128rpx;
		left: 0;
		top: 120rpx;
		padding: 0 30rpx;
		box-sizing: border-box;
		display: flex;
		align-items: center;
	}

	.tui-avatar {
		flex-shrink: 0;
		width: 128rpx;
		height: 128rpx;
		display: block;
	}

	.tui-info {
		width: 60%;
		padding-left: 30rpx;

	}

	.tui-nickname {
		font-size: 30rpx;
		font-weight: 500;
		color: #fff;
		display: flex;
		align-items: center;
	}

	.tui-img-vip {
		width: 56rpx;
		height: 24rpx;
		margin-left: 18rpx;
	}

	.tui-explain {
		width: 80%;
		font-size: 24rpx;
		font-weight: 400;
		color: #fff;
		opacity: 0.75;
		padding-top: 8rpx;
		white-space: nowrap;
		overflow: hidden;
		text-overflow: ellipsis;
	}

	.tui-btn-edit {
		flex-shrink: 0;
		padding-right: 22rpx;
	}

	.tui-header-btm {
		width: 100%;
		padding: 0 30rpx;
		box-sizing: border-box;
		position: absolute;
		left: 0;
		top: 280rpx;
		display: flex;
		align-items: center;
		justify-content: space-between;
		color: #fff;
	}

	.tui-btm-item {
		flex: 1;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.tui-btm-num {
		font-size: 32rpx;
		font-weight: 600;
		position: relative;
	}

	.tui-btm-text {
		font-size: 24rpx;
		opacity: 0.85;
		padding-top: 4rpx;
	}

	.tui-content-box {
		width: 100%;
		padding: 0 30rpx;
		box-sizing: border-box;
		position: relative;
		top: -72rpx;
		z-index: 10;
	}

	.tui-box {
		width: 100%;
		background: #fff;
		box-shadow: 0 3rpx 20rpx rgba(183, 183, 183, 0.1);
		border-radius: 10rpx;
		overflow: hidden;
	}

	.tui-order-box {
		height: 208rpx;
	}

	.tui-cell-header {
		width: 100%;
		height: 74rpx;
		padding: 0 26rpx;
		box-sizing: border-box;
		display: flex;
		align-items: center;
		justify-content: space-between;
	}

	.tui-cell-title {
		font-size: 30rpx;
		line-height: 30rpx;
		font-weight: 600;
		color: #333;
	}

	.tui-cell-sub {
		font-size: 26rpx;
		font-weight: 400;
		color: #999;
		padding-right: 28rpx;
	}

	.tui-order-list {
		width: 100%;
		height: 134rpx;
		padding: 0 30rpx;
		box-sizing: border-box;
		display: flex;
		align-items: center;
		justify-content: space-between;

	}

	.tui-order-item {
		flex: 1;
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	.tui-order-text,
	.tui-tool-text {
		font-size: 26rpx;
		font-weight: 400;
		color: #666;
		padding-top: 4rpx;
	}

	.tui-tool-text {
		font-size: 24rpx;
	}

	.tui-order-icon {
		width: 56rpx;
		height: 56rpx;
		display: block;
	}

	.tui-assets-box {
		height: 178rpx;
		margin-top: 20rpx;
	}

	.tui-assets-list {
		height: 84rpx;
	}

	.tui-assets-num {
		font-size: 32rpx;
		font-weight: 500;
		color: #333;
		position: relative;
	}

	.tui-assets-text {
		font-size: 24rpx;
		font-weight: 400;
		color: #666;
		padding-top: 6rpx;
	}

	.tui-tool-box {
		margin-top: 20rpx;
	}

	.tui-flex-wrap {
		flex-wrap: wrap;
		height: auto;
		padding-bottom: 30rpx;
	}

	.tui-tool-item {
		width: 25%;
		display: flex;
		align-items: center;
		justify-content: center;
		flex-direction: column;
		padding-top: 30rpx;
	}

	.tui-tool-icon {
		width: 64rpx;
		height: 64rpx;
		display: block;
	}

	.tui-badge-icon {
		width: 66rpx;
		height: 30rpx;
		position: absolute;
		right: 0;
		transform: translateX(88%);
		top: -15rpx;
	}

	/*为你推荐*/
	.tui-product-list {
		display: flex;
		justify-content: space-between;
		flex-direction: row;
		flex-wrap: wrap;
		box-sizing: border-box;
	}

	.tui-product-container {
		flex: 1;
		margin-right: 2%;
	}

	.tui-product-container:last-child {
		margin-right: 0;
	}

	.tui-pro-item {
		width: 100%;
		margin-bottom: 4%;
		background: #fff;
		box-sizing: border-box;
		border-radius: 12rpx;
		overflow: hidden;
	}

	.tui-pro-img {
		width: 100%;
		display: block;
	}

	.tui-pro-content {
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		box-sizing: border-box;
		padding: 20rpx;
	}

	.tui-pro-tit {
		color: #2e2e2e;
		font-size: 26rpx;
		word-break: break-all;
		overflow: hidden;
		text-overflow: ellipsis;
		display: -webkit-box;
		-webkit-box-orient: vertical;
		-webkit-line-clamp: 2;
	}

	.tui-pro-price {
		padding-top: 18rpx;
	}

	.tui-sale-price {
		font-size: 34rpx;
		font-weight: 500;
		color: #e41f19;
	}

	.tui-factory-price {
		font-size: 24rpx;
		color: #a0a0a0;
		text-decoration: line-through;
		padding-left: 12rpx;
	}

	.tui-pro-pay {
		padding-top: 10rpx;
		font-size: 24rpx;
		color: #656565;
	}

	.tui-btn-back {
		width: 88rpx;
		height: 88rpx;
		font-size: 26rpx;
		display: flex;
		align-items: center;
		justify-content: center;
		border-radius: 50%;
		background-color: rgba(0, 0, 0, .5);
		color: #fff;
		position: fixed;
		bottom: 60rpx;
		right: 30rpx;
		z-index: 9999;
	}

	/* ADD */
	.container {
		padding-bottom: env(safe-area-inset-bottom);
	}

	.tui-item-box {
		width: 100%;
		display: flex;
		align-items: center;
	}

	.tui-list-cell_name {
		padding-left: 20rpx;
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.tui-ml-auto {
		margin-left: auto;
	}

	.tui-right {
		margin-left: auto;
		margin-right: 34rpx;
		font-size: 26rpx;
		color: #999;
	}

	.tui-logo {
		height: 52rpx;
		width: 52rpx;
		flex-shrink: 0;
	}

	.tui-flex {
		display: flex;
		align-items: center;
	}

	.tui-msg-box {
		display: flex;
		align-items: center;
	}

	.tui-msg-pic {
		width: 100rpx;
		height: 100rpx;
		border-radius: 50%;
		display: block;
		margin-right: 24rpx;
		flex-shrink: 0;
	}

	.tui-msg-item {
		max-width: 500rpx;
		min-height: 80rpx;
		overflow: hidden;
		display: flex;
		flex-direction: column;
		justify-content: space-between;
	}

	.tui-msg-name {
		overflow: hidden;
		white-space: nowrap;
		text-overflow: ellipsis;
		font-size: 34rpx;
		line-height: 1;
		color: #262b3a;
	}

	.tui-msg-content {
		overflow: hidden;
		white-space: nowrap;
		text-overflow: ellipsis;
		font-size: 26rpx;
		line-height: 1;
		color: #9397a4;
	}

	.tui-msg-right {
		max-width: 120rpx;
		height: 88rpx;
		margin-left: auto;
		text-align: right;
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		align-items: flex-end;
	}

	.tui-right-dot {
		height: 76rpx !important;
		padding-bottom: 10rpx !important;

	}

	.tui-msg-time {
		width: 100%;
		font-size: 24rpx;
		line-height: 24rpx;
		color: #9397a4;
	}

	.tui-right-btn {
		height: 25px;
		width: 50px;
		box-sizing: border-box;
		margin-left: auto;
		margin-right: 0;
		font-size: 14px;
		color: rgb(5, 129, 255) !important;
		border: 1px solid rgb(5, 129, 255) !important;
		background: #fff !important;
		padding: 3px 11px;
		font-size: 13px;
		border-radius: 5px;
	}

	/* header */
	.tui-section-card {
		display: flex;
		align-items: center;
		flex-flow: column wrap;
		color: #fff;
		padding: 16px;
		background-color: rgb(5, 129, 255);
	}

	.g-image {
		width: 82px;
		height: 82px;
		border-radius: 100%;
		border: 2px solid #fff;
	}

	.tui-btn-box {
		width: 100%;
		display: flex;
		align-items: center;
		flex-flow: row wrap;
		justify-content: center;
	}

	.tui-btn-primary {
		/* display: block; */
		margin-top: 16px !important;
		color: #fff;
		border: solid 1px #e1e1e1 !important;
		border-radius: 40px;
		background-color: rgb(5, 129, 255) !important;
		font-size: 18px;
		width: 50% !important;
		box-shadow: 1px 1px 2px 0px #666;
	}
	.list-image{
		width:25px;
		height:25px;
	}
	.tui-btn-service {
			width: 88rpx;
			height: 88rpx;
			font-size: 26rpx;
			display: flex;
			align-items: center;
			justify-content: center;
			border-radius: 50%;
			background-color: rgba(0, 0, 0, .5);
			color: #fff;
			position: fixed;
			bottom: 50px;
			right: 30rpx;
			z-index: 9999;
		}
		.tui-my-bg{
			border-radius: 50%;
		}
</style>
