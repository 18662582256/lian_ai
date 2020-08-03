<template>
	<view class="container">
		<view class="tui-searchbox">
			<view class="tui-search-input" @tap="search">
				<view style="margin-left:20px">
					<icon type="search" :size="18" color="#999" style="vertical-align: middle;"></icon>
					<text class="tui-search-text">输入搜索关键词</text>
				</view>
				<tui-button width="200rpx" height="45px" :size="30" shape="circle">一键查找</tui-button>
			</view>
		</view>
		<view class="tui-photo">
			<view class="tui-photo-item" v-for="(item,index) in 18" :key="index" @click="detail">
				<img :src="'/static/images/mall/photodb/'+ img" />
			</view>
		</view>
		<tui-modal :show="modal" custom="true" width="100%" height="100%" padding="0 0" style="opacity:1 !important">
			<view class="tui-modal-img" @click="handleClick" @cancel="hide">
				<img :src="'/static/images/mall/photodb/'+ img" />
			</view>
		</tui-modal>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				dataList:[["1.jpg"]],
				img:"1.jpg",
				modal: false,
			}
		},
		methods: {
			detail: function(e) {
				this.modal = true;
			},
			hide:function(e){
				this.modal = false;
			},
			handleClick(e) {
				
				this.hide();
			},
		}
	}
</script>

<style>
	.container {
		padding-bottom: env(safe-area-inset-bottom);
	}
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
		flex: 1;
		color: #333;
		padding: 0 16rpx;
		font-size: 28rpx;
	}
	
	.tui-input-plholder {
		font-size: 28rpx;
		color: #b2b2b2;
	}

	.tui-photo{
		display: flex;
		flex-wrap: wrap;
		justify-content: space-between;
		background-color: #fff;
	}
	.tui-photo-item{
		width: 137px;
		height: 137px;
		margin-bottom: 1px;
	}
	.tui-photo-item>*{
		background-image:none;
	}
	.tui-photo-item img{
		width: 137px;
		height: 137px;
	}
	.tui-grid-label {
		display: block;
		text-align: center;
		font-weight: 400;
		color: #333;
		font-size: 28rpx;
		white-space: nowrap;
		overflow: hidden;
		text-overflow: ellipsis;
		margin-top: 10rpx;
	}
	.tui-grid-label-5 {
		margin-top: 0 !important;
		color: #8a5966 !important;
	}
	.tui-modal-img{
		width:100%;
		background-color: rgba(0, 0, 0, 1) !important;
	}
	>>>.tui-modal-mask {
		background-color: rgba(0, 0, 0, 1) !important;
	}
	
</style>
