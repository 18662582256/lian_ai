<template>
	<view class="container">
		<tui-tabs :tabs="navbar" :currentTab="currentTab>1?0:currentTab" @change="change" itemWidth="50%"></tui-tabs>
		<view class="tui-list tui-combat" v-if="!currentTab">
			<tui-list-cell :lineLeft="false" @click="detail">
				<view class="tui-item-box">
					<view class="tui-msg-box">
						<image src="/static/images/mall/case/tabs1.jpg" class="tui-msg-pic" mode="widthFix"></image>
						<view class="tui-msg-item">
							301期：网上撩妹怎么聊？老司来给你带带路
						</view>
					</view>
				</view>
			</tui-list-cell>
			<tui-list-cell :lineLeft="false" @click="detail">
				<view class="tui-item-box">
					<view class="tui-msg-box">
						<image src="/static/images/mall/case/tabs1.jpg" class="tui-msg-pic" mode="widthFix"></image>
						<view class="tui-msg-item">
							301期：网上撩妹怎么聊？老司来给你带带路
						</view>
					</view>
				</view>
			</tui-list-cell>
			<tui-list-cell :lineLeft="false" @click="detail">
				<view class="tui-item-box">
					<view class="tui-msg-box">
						<image src="/static/images/mall/case/tabs2.jpg" class="tui-msg-pic" mode="widthFix"></image>
						<view class="tui-msg-item">
							301期：网上撩妹怎么聊？老司来给你带带路
						</view>
					</view>
				</view>
			</tui-list-cell>
		</view>
		<view class="tui-list tui-tutorials" v-else>
			<tui-list-cell :lineLeft="false" @click="detail">
				<view class="tui-item-box">
					<view class="tui-msg-box">
						<image src="/static/images/mall/case/tabs3.jpg" class="tui-msg-pic" mode="widthFix"></image>
						<view class="tui-msg-item">
							301期：网上撩妹怎么聊？老司来给你带带路
						</view>
					</view>
				</view>
			</tui-list-cell>
			<tui-list-cell :lineLeft="false" @click="detail">
				<view class="tui-item-box">
					<view class="tui-msg-box">
						<image src="/static/images/mall/case/tabs4.jpg" class="tui-msg-pic" mode="widthFix"></image>
						<view class="tui-msg-item">
							301期：网上撩妹怎么聊？老司来给你带带路
						</view>
					</view>
				</view>
			</tui-list-cell>
			<tui-list-cell :lineLeft="false" @click="detail">
				<view class="tui-item-box">
					<view class="tui-msg-box">
						<image src="/static/images/mall/case/tabs5.jpg" class="tui-msg-pic" mode="widthFix"></image>
						<view class="tui-msg-item">
							301期：网上撩妹怎么聊？老司来给你带带路
						</view>
					</view>
				</view>
			</tui-list-cell>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				currentTab: 0,
				backgroundColor: "linear-gradient(90deg, rgb(255, 118, 38), rgb(252, 30, 82))",
				navbar: [{
					name: "聊天实战"
				}, {
					name: "绝密教程"
				}],
				tabList1:[{}]
			}
		},
		methods: {
			change(e) {
				this.currentTab = e.index
			},
			detail: function() {
				this.tui.toast("click~")
			}
		
		}
	}
</script>

<style>
.container {
		padding-bottom: env(safe-area-inset-bottom);
	}

	.tui-item-box {
		width: 100%;
		display: flex;
		align-items: center;
		flex-flow: row nowrap;
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
		flex-basis: 115px;
		width: 115px;
		height: 82px !important;
		margin-right: 11px;
		border-radius:5px;
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
</style>
