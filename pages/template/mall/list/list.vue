<template>
	<view class="container">
		<view class="tui-searchbox">
			<view class="tui-search-input" @tap="search">
				<view style="margin-left:20px">
					<icon type="search" :size="18" color="#999"></icon>
					<input confirm-type="search" placeholder="一键复制搜索解决尴尬问题" :focus="true"auto-focus placeholder-class="tui-input-plholder"
					 class="tui-input tui-search-text" v-model.trim="key" @input="inputKey"/>
				</view>
				<tui-button width="200rpx" height="45px" :size="30" shape="circle">一键查找</tui-button>
			</view>
		</view>
		<tui-list-view>
			<tui-list-cell v-for="(items,index) in list" :key="index">
				<view class="tui-item-box" v-for="(item,i) in items" :key="i">
					<image v-if="item.sex=='male'" src="/static/images/mall/list/male.png" class="tui-logo"></image>
					<image v-else src="/static/images/mall/list/female.png" class="tui-logo"></image>
					<text class="tui-list-cell_name">{{item.content}}</text>
					<view class="tui-right tui-title" @click="clipboard(item)">复制</view>
				</view>
			</tui-list-cell>
			
			
			
		</tui-list-view>
	</view>
</template>

<script>
	const thorui = require("@/components/common/tui-clipboard/tui-clipboard.js")
	export default {
		data() {
			return {
				list: [
					[{
							sex: "male",
							content: "地球和太阳都不是宇宙的中心，你才是1111"
						},
						{
							sex: "female",
							content: "地球和太阳都不是宇宙的中心，你才是2222"
						},
						{
							sex: "male",
							content: "地球和太阳都不是宇宙的中心，你才是3333"
						},
						{
							sex: "female",
							content: "地球和太阳都不是宇宙的中心，你才是4444444"
						},
					],
					[{
							sex: "male",
							content: "地球和太阳都不是宇宙的中心，你才是555"
						},
						{
							sex: "female",
							content: "地球和太阳都不是宇宙的中心，你才是666"
						},
						{
							sex: "male",
							content: "地球和太阳都不是宇宙的中心，你才是777"
						},
						{
							sex: "female",
							content: "地球和太阳都不是宇宙的中心，你才是8888"
						},
					],
					[{
							sex: "male",
							content: "地球和太阳都不是宇宙的中心，你才是99"
						},
						{
							sex: "female",
							content: "地球和太阳都不是宇宙的中心，你才是1010"
						},
						{
							sex: "male",
							content: "地球和太阳都不是宇宙的中心，你才是11111"
						},
						{
							sex: "female",
							content: "地球和太阳都不是宇宙的中心，你才是122121"
						},
					],
				]

			}
		},
		methods: {
			scroll(e) {
				//动画时长固定300ms
				if (!this.isScroll) {
					setTimeout(() => {
						this.isScroll = true;
					}, 150);
				} else {
					this.scrollTop = e.detail.scrollTop;
				}
			},
			clipboard: function(event) {
				let data = event.content;
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
		}
	}
</script>

<style>
	.tui-searchbox {
		padding: 30rpx 10px;
		box-sizing: border-box;
		display: flex;
		align-items: center;
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

	.tui-input {
		/* flex: 1; */
		height:100%;
		color: #333;
		padding: 0 16rpx;
		font-size: 28rpx;
	}

	.tui-input-plholder {
		font-size: 28rpx;
		color: #b2b2b2;
	}

	.tui-item-box {
		width: 100%;
		display: flex;
		align-items: center;
		margin-bottom: 10px;
	}

	.tui-list-cell_name {
		padding-left: 20rpx;
		display: flex;
		align-items: center;
		justify-content: center;
		flex-basis: 70%;
	}

	.tui-ml-auto {
		margin-left: auto;
	}

	.tui-right {
		height: 25px;
		width: 50px;
		box-sizing: border-box;
		margin-left: auto;
		margin-right: 34rpx;
		font-size: 26rpx;
		color: rgb(5, 129, 255) !important;
		border: 1px solid rgb(5, 129, 255) !important;
		background: #fff !important;
		padding: 3px 11px;
		font-size: 13px;
		border-radius: 5px;
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

	>>>.tui-line-left::after {
		left: 0 !important;
	}
	.tui-search-input{
		display:flex;
		align-items:center;
		justify-content: space-between;
	}
</style>
