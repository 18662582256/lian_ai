<template>
	<view class="container">
		<!--tabbar-->
		<view class="tui-tabbar">
			<block v-for="(item, index) in tabbar" :key="index">
				<view class="tui-tabbar-item" :data-index="index" @tap="tabbarSwitch(index)">
					<view :class="[index ==0 ? 'tui-ptop-4' : '']">
						<image :src="'/static/images/mall/tabbar/' + item.img" class="tui-tabbar-img" mode="scaleToFill"></image>
					</view>
					<view class="tui-scale">{{ item.text }}</view>
				</view>
			</block>
		</view>
		<!--tabbar-->
		<!--header-->
		<view class="tui-header">
			<view class="tui-text">恋爱大神话术</view>
		</view>
		<!--header-->
		<view class="tui-banner-bg">
			<!-- <view class="tui-primary-bg tui-route-left"></view>
				<view class="tui-primary-bg tui-route-right"></view> -->
			<!--banner-->
			<view class="tui-banner-box">
				<swiper :indicator-dots="true" :autoplay="true" :interval="5000" :duration="150" class="tui-banner-swiper"
				 :circular="true" indicator-color="rgba(255, 255, 255, 0.8)" indicator-active-color="#fff">
					<swiper-item v-for="(item, index) in banner" :key="index" @tap.stop="detail">
						<image :src="'/static/images/mall/banner/' + item" class="tui-slide-image" mode="scaleToFill" />
					</swiper-item>
				</swiper>
			</view>
		</view>

		<view class="tui-searchbox">
			<view class="tui-search-input" @tap="search">
				<view style="margin-left:20px">
					<icon type="search" :size="18" color="#999" style="vertical-align: middle;"></icon>
					<text class="tui-search-text">一键复制搜索解决尴尬问题</text>
				</view>
				<tui-button width="200rpx" height="45px" :size="30" shape="circle">一键查找</tui-button>
			</view>
		</view>
		<view class="tui-search-bottom-text">
			<text>100W+恋爱话术，免费进群</text>
			<text>今日更新1875条</text>
		</view>

		<view class="tui-product-category">
			<view class="tui-category-item" v-for="(item, index) in category" :key="index" :data-key="item.name" @tap="more(index)">
				<image :src="'/static/images/mall/category/' + item.img" class="tui-category-img" mode="scaleToFill"></image>
				<view class="tui-category-name">{{ item.name }}</view>
			</view>
		</view>

		<view class="tag-list">
			<view class="item" v-for="(item,index) in tags" :key="index">
				<view class="item-name">{{item.name}}</view>
				<view class="tui-list">
					<view class="tui-item" v-for="(list,i) in item.list" :key="i" @tap="toListPage">{{list}}</view>
				</view>

			</view>
		</view>
		<text class="tui-copyright">恋爱大神话术版权所有</text>
		<view class="tui-btn-service" @tap="back">
			<image src='/static/images/mall/kefu.png' class="tui-my-bg" mode="widthFix"></image>
		</view>
	</view>
</template>
<script>
	export default {
		data() {
			return {
				current: 0,
				tabbar: [{
						icon: 'home',
						img:'1.png',
						text: '恋爱话术',
						size: 48
					},
					{
						icon: 'manage',
						img:'2.png',
						text: '聊天案例',
						size: 54
					},
					{
						icon: 'cart',
						img:'3.png',
						text: '学堂',
						size: 48
					},
					{
						icon: 'people',
						img:'4.png',
						text: '个人中心',
						size: 52
					}
				],
				banner: ['1.png', '2.png'],
				category: [{
						img: '1.png',
						name: '朋友圈素材'
					},
					{
						img: '6.png',
						name: '土味情话'
					},
					{
						img: '3.png',
						name: 'AI导师'
					},
					{
						img: '4.png',
						name: '会员激活'
					},
					{
						img: '5.png',
						name: '开场白'
					},
					{
						img: '2.png',
						name: '浪漫邀约'
					},
					{
						img: '7.png',
						name: '牵手接吻'
					},
					{
						img: '8.png',
						name: '确定恋爱'
					}
				],
				tags: [{
					name: "恋爱表白",
					list: ["好奇开场", "直白开场", "间接开场", "开场惯例", "惯例开场", "趣味开场", "表情开场", "土味情话", "重新开场"]
				}, {
					name: "幽默互动",
					list: ["联系感建立", "价值型聊天", "影视综艺话梗", "手相签名冷读", "共鸣故事", "情感链接", "冷读语录", "幽默聊天", "颜色星座冷读", "生活分享"]
				}, {
					name: "温暖关怀",
					list: ["风趣自然", "讲故事", "情感波动"]
				}, {
					name: "暖心交流",
					list: ["正反冷读", "话块连清", "聊天交流"]
				}, {
					name: "浪漫约会",
					list: ["约会套路", "促成邀约", "预期建立", "模糊邀约", "约会后续话术", "浪漫创意约会", "约会冷场", "约会互动", "约会碰面"]
				}, {
					name: "惯例学习",
					list: ["现场聊天交流", "异议处理", "名人配文", "朋友圈配文", "互动类别", "自夸类别"]
				}],
				
				
				pageIndex: 1,
				loadding: false,
				pullUpOn: true
			};
		},
		methods: {
			tabbarSwitch: function(e) {
				if (e != 0) {
					if (e == 1) {
						uni.navigateTo({
							url: '../case/case'
						});
					} else if (e == 2) {
						uni.navigateTo({
							url: '../school/school'
						});
					} else {
						uni.navigateTo({
							url: '../my/my'
						});
					}
				}
			},
			detail: function() {
				uni.navigateTo({
					url: '../productDetail/productDetail'
				});
			},
			coupon() {
				uni.navigateTo({
					url: '../coupon/coupon'
				});
			},
			classify: function() {
				uni.navigateTo({
					url: '../case/case'
				});
			},
			more: function(e) {
				if(e==0){
					uni.navigateTo({
						url: '../classify/classify'
					});
				}else if(e==2 || e==3){
					uni.navigateTo({
						url: '../login/login'
					});
				}else{
					uni.navigateTo({
						url: '../list/list'
					});
				}
				
			},
			toListPage:function(){
				uni.navigateTo({
					url: '../list/list'
				});
			},
			search: function() {
				uni.navigateTo({
					url: '../search/search'
				});
			}
		},
		onPullDownRefresh: function() {
			let loadData = JSON.parse(JSON.stringify(this.productList));
			loadData = loadData.splice(0, 10);
			this.productList = loadData;
			this.pageIndex = 1;
			this.pullUpOn = true;
			this.loadding = false;
			uni.stopPullDownRefresh();
		},
		onReachBottom: function() {
			if (!this.pullUpOn) return;
			this.loadding = true;
			if (this.pageIndex == 4) {
				this.loadding = false;
				this.pullUpOn = false;
			} else {
				let loadData = JSON.parse(JSON.stringify(this.productList));
				loadData = loadData.splice(0, 10);
				if (this.pageIndex == 1) {
					loadData = loadData.reverse();
				}
				this.productList = this.productList.concat(loadData);
				this.pageIndex = this.pageIndex + 1;
				this.loadding = false;
			}
		}
	};
</script>

<style>
	page {
		background-color: #f7f7f7;
	}

	.container {
		padding-bottom: 100rpx;
		color: #333;
	}

	/*tabbar*/

	.tui-tabbar {
		width: 100%;
		position: fixed;
		display: flex;
		align-items: center;
		justify-content: space-between;
		z-index: 99999;
		background: #fff;
		height: 100rpx;
		left: 0;
		bottom: 0;
		padding-bottom: env(safe-area-inset-bottom);
	}

	.tui-safearea-bottom {
		width: 100%;
		height: env(safe-area-inset-bottom);
	}

	.tui-tabbar::before {
		content: '';
		width: 100%;
		border-top: 1rpx solid #d9d9d9;
		position: absolute;
		top: 0;
		left: 0;
		-webkit-transform: scaleY(0.5);
		transform: scaleY(0.5);
	}

	.tui-tabbar-item {
		flex: 1;
		width: 25%;
		display: flex;
		align-items: center;
		flex-direction: column;
		justify-content: center;
		font-size: 24rpx;
		color: #666;
		height: 80rpx;
	}

	.tui-ptop-4 {
		padding-top: 4rpx;
	}

	.tui-scale {
		font-weight: bold;
		transform: scale(0.8);
		transform-origin: center 100%;
		line-height: 30rpx;
	}

	.tui-item-active {
		color: #e41f19 !important;
	}

	/*tabbar*/

	.tui-header {
		width: 100%;
		height: 44px;
		padding: 0 30rpx 0 20rpx;
		box-sizing: border-box;
		background-color: #f1f1f1;
		display: flex;
		align-items: center;
		justify-content: space-between;
		position: fixed;
		left: 0;
		top: 0;
		/* #ifdef H5 */
		top: 0;
		/* #endif */
		z-index: 999;
		text-align: center;
	}

	.tui-rolling-search {
		width: 100%;
		height: 60rpx;
		border-radius: 35rpx;
		padding: 0 40rpx 0 30rpx;
		box-sizing: border-box;
		background-color: #fff;
		display: flex;
		align-items: center;
		flex-wrap: nowrap;
		color: #999;
	}

	.tui-category {
		font-size: 24rpx;
		color: #fff;
		display: flex;
		align-items: center;
		justify-content: center;
		flex-direction: column;
		margin: 0;
		margin-right: 22rpx;
		flex-shrink: 0;
	}

	.tui-category-scale {
		transform: scale(0.7);
		line-height: 24rpx;
	}

	.tui-icon-category {
		line-height: 20px !important;
		margin-bottom: 0 !important;
	}

	.tui-swiper {
		font-size: 26rpx;
		height: 60rpx;
		flex: 1;
		padding-left: 12rpx;
	}

	.tui-swiper-item {
		display: flex;
		align-items: center;
	}

	.tui-hot-item {
		line-height: 26rpx;
		white-space: nowrap;
		overflow: hidden;
		text-overflow: ellipsis;
	}

	.tui-header-banner {
		padding-top: 100rpx;
		box-sizing: border-box;
		background: transparent;
	}

	.tui-hot-search {
		color: #fff;
		font-size: 24rpx;
		display: flex;
		align-items: center;
		justify-content: space-between;
		padding: 0 20rpx;
		box-sizing: border-box;
		position: relative;
		z-index: 2;
	}

	.tui-hot-tag {
		background-color: rgba(255, 255, 255, 0.15);
		padding: 10rpx 24rpx;
		border-radius: 30rpx;
		display: flex;
		align-items: center;
		justify-content: center;
		line-height: 24rpx;
	}

	.tui-banner-bg {
		display: flex;
		height: 193px;
		padding-top: 55px;
		background-color: #fff;
		position: relative;
	}

	.tui-primary-bg {
		width: 50%;
		display: inline-block;
		height: 224rpx;
		border: 1px solid transparent;
		position: relative;
		z-index: 1;
		background-color: transparent;
	}

	.tui-route-left {
		transform: skewY(8deg);
	}

	.tui-route-right {
		transform: skewY(-8deg);
	}

	.tui-banner-box {
		width: 100%;
		height: 100%;
		padding: 0 20rpx;
		box-sizing: border-box;
		background-color: #fff;
		position: absolute;
		/* overflow: hidden; */
		z-index: 99;
		left: 0;
	}

	.tui-banner-swiper {
		width: 100%;
		height: 100%;
		border-radius: 12rpx;
		overflow: hidden;
		transform: translateY(0);
	}

	.tui-slide-image {
		width: 100%;
		height: 100%;
		display: block;
	}

	/* #ifdef MP-WEIXIN */
	.tui-banner-swiper .wx-swiper-dot {
		width: 8rpx;
		height: 8rpx;
		display: inline-flex;
		background: none;
		justify-content: space-between;
	}

	.tui-banner-swiper .wx-swiper-dot::before {
		content: '';
		flex-grow: 1;
		background-color: rgba(255, 255, 255, 0);
		border-radius: 16rpx;
		overflow: hidden;
	}

	.tui-banner-swiper .wx-swiper-dot-active::before {
		background-color: #fff;
	}

	.tui-banner-swiper .wx-swiper-dot.wx-swiper-dot-active {
		width: 16rpx;
	}

	/* #endif */

	/* #ifndef MP-WEIXIN */
	>>>.tui-banner-swiper .uni-swiper-dot {
		width: 8rpx;
		height: 8rpx;
		display: inline-flex;
		background-color: none;
		justify-content: space-between;
	}

	>>>.tui-banner-swiper .uni-swiper-dot::before {
		content: '';
		flex-grow: 1;
		background-color: rgba(255, 255, 255, 0);
		border-radius: 16rpx;
		overflow: hidden;
	}

	>>>.tui-banner-swiper .uni-swiper-dot-active::before {
		background-color: #fff;
	}

	>>>.tui-banner-swiper .uni-swiper-dot.uni-swiper-dot-active {
		width: 16rpx;
	}

	/* #endif */

	.tui-product-category {
		background-color: #fff;
		padding: 0rpx 20rpx 30rpx 20rpx;
		box-sizing: border-box;
		display: flex;
		align-items: center;
		justify-content: space-between;
		flex-wrap: wrap;
		font-size: 24rpx;
		color: #555;
	}

	.tui-category-item {
		width: 25%;
		height: 118rpx;
		display: flex;
		align-items: center;
		justify-content: space-between;
		flex-direction: column;
		padding-top: 30rpx;
	}

	.tui-category-img {
		height: 80rpx;
		width: 80rpx;
		display: block;
	}
	.tui-tabbar-img{
		display: block;
		width:28px;
		height:28px;
	}

	.tui-category-name {
		line-height: 24rpx;
	}

	.tui-product-box {
		margin-top: 20rpx;
		padding: 0 20rpx;
		box-sizing: border-box;
	}

	.tui-pb-20 {
		padding-bottom: 20rpx;
	}

	.tui-bg-white {
		background-color: #fff;
	}

	.tui-group-name {
		width: 100%;
		font-size: 32rpx;
		font-weight: bold;
		text-align: center;
		padding: 24rpx 0;
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.tui-activity-box {
		display: flex;
		border-radius: 12rpx;
		overflow: hidden;
	}

	.tui-activity-img {
		width: 50%;
		display: block;
	}

	.tui-new-box {
		display: flex;
		align-items: center;
		justify-content: space-between;
		flex-wrap: wrap;
	}

	.tui-new-item {
		width: 49%;
		height: 200rpx;
		padding: 0 20rpx;
		box-sizing: border-box;
		display: flex;
		align-items: center;
		background: #f5f2f9;
		position: relative;
		border-radius: 12rpx;
	}

	.tui-new-mtop {
		margin-top: 2%;
	}

	.tui-title-box {
		font-size: 24rpx;
	}

	.tui-new-title {
		line-height: 32rpx;
		word-break: break-all;
		overflow: hidden;
		text-overflow: ellipsis;
		display: -webkit-box;
		-webkit-box-orient: vertical;
		-webkit-line-clamp: 2;
	}

	.tui-new-price {
		padding-top: 18rpx;
	}

	.tui-new-present {
		color: #ff201f;
		font-weight: bold;
	}

	.tui-new-original {
		display: inline-block;
		color: #a0a0a0;
		text-decoration: line-through;
		padding-left: 12rpx;
		transform: scale(0.8);
		transform-origin: center center;
	}

	.tui-new-img {
		width: 160rpx;
		height: 160rpx;
		display: block;
		flex-shrink: 0;
	}

	.tui-new-label {
		width: 56rpx;
		height: 56rpx;
		border-top-left-radius: 12rpx;
		position: absolute;
		left: 0;
		top: 0;
	}

	.tui-product-list {
		display: flex;
		justify-content: space-between;
		flex-direction: row;
		flex-wrap: wrap;
		box-sizing: border-box;
		/* padding-top: 20rpx; */
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

	.tui-text {
		display: block;
		width: 100%;
		font-weight: 700;
		font-size: 16px;
		color: #000;
		text-align: center;
	}

	.tui-searchbox {
		width: 100%;
		height: 70px;
		padding: 0 30rpx;
		box-sizing: border-box;
		background: #fff;
		display: flex;
		align-items: center;
		justify-content: center;
		/* #ifdef H5
	/* top: 44px; */
		/* #endif */
		z-index: 100;
	}

	.tui-searchbox::after {
		content: '';
		position: absolute;
		border-bottom: 1rpx solid #d2d2d2;
		-webkit-transform: scaleY(0.5);
		transform: scaleY(0.5);
		bottom: 0;
		right: 0;
		left: 0;
	}

	.tui-search-input {
		width: 100%;
		height: 45px;
		background: #fff;
		border-radius: 22px;
		border: 1px solid #f1f1f1;
		font-size: 26rpx;
		color: #999;
		display: flex;
		align-items: center;
		justify-content: space-between;
	}

	.tui-search-text {
		padding-left: 8px;
	}

	.tui-search-bottom-text {
		display: flex;
		align-items: center;
		justify-content: space-between;
		padding: 0 16px 11px;
		background-color: #fff;
		color: rgb(5, 129, 255);
		font-size: 15px;
	}

	.tag-list {
		padding: 0 11px;
		background-color: #fff;
	}

	.tag-list .item {
		display: flex;
		-webkit-box-orient: vertical;
		-webkit-box-direction: normal;
		-webkit-flex-flow: column wrap;
		flex-flow: column wrap;
		background: #fff;
		padding: 11px 0 11px;
	}
	.item-name{
		display: flex;
		-webkit-box-orient: horizontal;
		-webkit-box-direction: normal;
		-webkit-flex-flow: row nowrap;
		flex-flow: row nowrap;
		-webkit-box-align: center;
		-webkit-align-items: center;
		align-items: center;
		padding: 0 16px;
		font-size:15px;
		color:#333;
	}
	.item-name:before{
		border-radius: 5px;
		width: 4px;
		background-color: rgb(5, 129, 255);
		height: 16px;
		margin-right: 8px;
		content:"";
	}
	 .tui-list{
		display: flex;
	    -webkit-box-orient: horizontal;
	    -webkit-box-direction: normal;
	    -webkit-flex-flow: row wrap;
	    flex-flow: row wrap;
	    -webkit-box-pack: justify;
	    -webkit-justify-content: space-between;
	    justify-content: space-between;
	    -webkit-align-content: baseline;
	    align-content: baseline;
	    padding: 0 11px;
}
.tui-item{
		display: flex;
	    -webkit-box-orient: horizontal;
	    -webkit-box-direction: normal;
	    -webkit-flex-flow: row nowrap;
	    flex-flow: row nowrap;
	    -webkit-box-pack: center;
	    -webkit-justify-content: center;
	    justify-content: center;
	    -webkit-box-align: center;
	    -webkit-align-items: center;
	    align-items: center;
	    font-size: 13px;
	    height: 35px;
	    color: #333;
		font-size: 14px;
		background-color: rgb(235, 248, 255);
		border-radius: 5px;
		border-width: 0px;
		margin: 11px 0 0;
		width: 28%;
}
.tui-copyright{
	    display: flex;
	    -webkit-box-orient: horizontal;
	    -webkit-box-direction: normal;
	    -webkit-flex-flow: row nowrap;
	    flex-flow: row nowrap;
	    -webkit-box-pack: center;
	    -webkit-justify-content: center;
	    justify-content: center;
	    -webkit-box-align: center;
	    -webkit-align-items: center;
	    align-items: center;
		margin-top:15px;
	    padding: 16px;
	    color: #8b8b8b;
	    font-size: 13px;
	    background-color: #fff;
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
		bottom: 75px;
		right: 30rpx;
		z-index: 9999;
	}
	.tui-my-bg{
		border-radius: 50%;
	}
</style>
