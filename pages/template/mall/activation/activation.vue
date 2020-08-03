<template>
	<view class="container">
		<image src="/static/images/mall/activation/1.jpg" class="list-image" />
		<view class="tui-vip-type">
			<view class="tui-vip-title">请选择VIP类型</view>
			<view class="tui-vip-list">
				<view class="item-box" v-for="(items,index) in vipType" :key="index" :class="[items.isSelect?'active':'']" @click="vipSelect(items)">
					<view class="item">
						<view class="tui-vip-header">{{items.name}}</view>
							<view class="tui-vip-price">
								<view class="tui-vip-unit">￥</view>
								{{items.price}}
								</view>
						<view class="tui-original_price">
							{{items.original}}元
						</view>
					</view>
				</view>
			</view>
		</view>
		<view class="tui-rolling-news">
			<swiper vertical autoplay circular interval="3000" class="tui-swiper">
				<swiper-item v-for="(item,index) in 10" :key="index" class="tui-swiper-item">
					<view class="tui-news-item">*****购买了永久会员</view>
				</swiper-item>
			</swiper>
		</view>
		<view class="tui-vip-privilege">
			<view class="tui-vip-title">畅享尊贵特权</view>
			<view class="tui-history-content">
				<block v-for="(item,index) in history" :key="index">
					<tui-tag margin="0 24rpx 24rpx 0" type="gray" shape="circle">{{item}}</tui-tag>
				</block>
			</view>
		</view>
		<view class="tui-notice">
			<view class="tui-notice-title">购买须知</view>
			<img src="/static/images/mall/activation/2.png" class="list-image" />
			<view class="tui-notice-list">1、购买后立即生效，重复购买会自动叠加VIP时长。</view>
			<view class="tui-notice-list">2、会员功能属于虚拟产品，购买后不支持退款。请仔细聊天本软件的功能后再进行购买</view>
			<view class="tui-notice-list">3、如果支付成功后没有成功开通或续费VIP，请尝试重新登录（一定要登录原帐号）</view>
		</view>
		
		
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				vipType:[{
					name:"年度会员（推荐）",
					price:59,
					original:99,
					isSelect:true
				},{
					name:"月度会员",
					price:39,
					original:59,
					isSelect:false
				},{
					name:"永久会员",
					price:79,
					original:299,
					isSelect:false
				},{
					name:"付款自动搭建小程序",
					price:3000,
					original:9800,
					isSelect:false
				}],
				newsList: [
					"致力发展负责",
					"格兰仕暗示拜访拼多多后",
					"阿里计划将每股普通股拆"
				],
				history: [
					"开通会员查看全部内容，并赠送绝密资料",
					"套路",
					"开场",
					"表情",
					"框架",
					"赞美",
					"厉害",
					"自恋",
					"小姐姐"
				],
				
			}
		},
		methods: {
			vipSelect(item) {
				this.vipType.forEach(function(items,index){
					items.isSelect=false;
				});
				item.isSelect=true;
			}
			
		}
	}
</script>

<style>
	.list-image{
		width:100%;
	}
	.tui-vip-type,
	.tui-vip-privilege,
	.tui-notice{
		padding: 0 16px 0px 16px;
		box-sizing: border-box;
	}
	.tui-vip-title{
		color: #444;
		font-weight: 700;
		font-size:15px;
		margin: 11px 0;
		padding-left: 16px;
		margin-bottom: 16px;
	}
	.tui-vip-header{
		font-weight: 700;
		font-size: 15px;
		text-align:center;
	}
	
	.tui-vip-list{
		display: flex;
		flex-wrap: wrap;
		justify-content: space-between;
	}
	.tui-vip-list .item-box{
		display: flex;
		align-items: center;
		flex-flow: row wrap;
		justify-content: center;
		position: relative;
		margin-bottom: 22px;
		flex-basis: 33.333%;
	}
	.tui-vip-list .item-box .item{
		position:relative;
		display: flex;
		flex-basis: 80%;
		flex-flow: column wrap;
		justify-content: center;
		align-items: center;
		border-radius: 5px;
		border: 1px solid #e1e1e1;
		background-color: #fff;
		padding: 10px;
		box-sizing:border-box;
	}
	.tui-vip-list .item-box.active .item{
		border-color:rgb(5, 129, 255);
	}
	.tui-vip-list .item-box.active .item:after{
		position: absolute;
		right: 0px;
		bottom: 0px;
		width: 0;
		height: 0;
		border-style: solid;
		border-width: 0 0 23px 23px;
		border-color: transparent transparent rgb(5, 129, 255);
		content:"";
	}
	.tui-vip-list .item-box.active .item:before{
		position: absolute;
		right: 0px;
		bottom: 0px;
		content:"√";
		font-size:16px;
		color:#fff;
		z-index:99;
		
	}
	.tui-vip-price{
		display:flex;
		align-items:center;
		position: relative;
		font-weight: 700;
		font-size: 24px;
		margin:5px 0;
		color: rgb(5, 129, 255);
	}
	.tui-vip-unit{
		font-size: 15px;
		position: absolute;
		left: -13px;
		bottom: 4px;
		cursor: pointer;
	}
	.tui-original_price{
		color: #7e7e7e;
		text-decoration: line-through;
		font-size: 15px;
	}
	.tui-rolling-news {
		width: 100%;
		padding: 12rpx 30rpx;
		box-sizing: border-box;
		display: flex;
		align-items: center;
		justify-content: center;
		flex-wrap: nowrap;
		text-align:center;
	}
	.tui-swiper {
		font-size: 28rpx;
		height: 50rpx;
		flex: 1;
	}
	
	.tui-swiper-item {
		display: flex;
		align-items: center;
		text-align:center;
	}
	
	.tui-news-item {
		line-height: 15px;
		text-align:center;
		margin:auto;
		white-space: nowrap;
		overflow: hidden;
		text-overflow: ellipsis;
		color:rgb(229,77,66);
		font-size:13px;
	}
	.tui-history-content{
		display: flex;
		align-items: center;
		flex-wrap: wrap;
	}
	.tui-tag{
		background:#fff !important;
		margin: 0 16px 16px 0;
		border: 1px solid #e2e2e2;
		padding: 8px 11px;
		border-radius: 5px;
	}
	.tui-notice-title{
		color: #444;
		font-weight: 700;
		font-size:15px;
		margin: 11px 0;
	}
	.tui-notice-list{
		color: rgb(153, 153, 153);
		font-size:15px;
	}

</style>
