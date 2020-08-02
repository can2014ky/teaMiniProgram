<template>
	<view class="mine-wrapper">
	  <view class="user-container">
	    <image src="/static/images/bg.png" class="bg"></image>
	    <view class="user-content">
	      <image src="/static/images/defaultAvatar.png" class="user-avatar"></image>
	      <view class="user-info">
	        <view v-if="true" class="login">登录/注册</view>
	        <view v-else class="login">颜路</view>
	      </view>
	    </view>
	  </view>
		<view class="message-container">
			<view class="item">
				<view class="number">3张(可用)</view>
				<view class="name">我的优惠券</view>
			</view>
			<view class="item">
				<view class="number">0</view>
				<view class="name">我的积分</view>
			</view>
		</view>
		<view class="common-container">
			<view class="top">
				<view class="title">我的订单</view>
				<view class="all">查看全部</view>
			</view>
			<view class="list-conatiner">
				<view class="item">
					<view class="">
						<image src="../../static/images/mineActive.png" mode=""></image>
					</view>
					<view class="">待成团</view>
				</view>
				<view class="item">
					<view class="">
						<image src="../../static/images/mineActive.png" mode=""></image>
					</view>
					<view class="">待付款</view>
				</view>
				<view class="item">
					<view class="">
						<image src="../../static/images/mineActive.png" mode=""></image>
					</view>
					<view class="">待发货</view>
				</view>
				<view class="item">
					<view class="">
						<image src="../../static/images/mineActive.png" mode=""></image>
					</view>
					<view class="">待收货</view>
				</view>
				<view class="item">
					<view class="">
						<image src="../../static/images/mineActive.png" mode=""></image>
					</view>
					<view class="">待评价</view>
				</view>
			</view>
		</view>
		<view class="common-container">
			<view class="top">
				<view class="title">常用功能</view>
			</view>
			<view class="common-list">
				<view class="item">
					<view class="">
						<image src="../../static/images/mineActive.png" mode=""></image>
					</view>
					<view class="">我的收藏</view>
				</view>
				<view class="item">
					<view class="">
						<image src="../../static/images/mineActive.png" mode=""></image>
					</view>
					<view class="">我的优惠券</view>
				</view>
				<view class="item">
					<view class="">
						<image src="../../static/images/mineActive.png" mode=""></image>
					</view>
					<view class="">我的积分</view>
				</view>
				<view class="item">
					<view class="">
						<image src="../../static/images/mineActive.png" mode=""></image>
					</view>
					<view class="">我的地址</view>
				</view>
				<view class="item">
					<view class="">
						<image src="../../static/images/mineActive.png" mode=""></image>
					</view>
					<view class="">会员中心</view>
				</view>
				<view class="item">
					<view class="">
						<image src="../../static/images/mineActive.png" mode=""></image>
					</view>
					<view class="">我的客服</view>
				</view>
				<view class="item">
					<view class="">
						<image src="../../static/images/mineActive.png" mode=""></image>
					</view>
					<view class="">我的推广码</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
</script>

<style lang="scss" scoped>
	.mine-wrapper {
	  background-color: #f5f5f9;
	  min-height: 100vh;
		.user-container {
		  height: 300rpx;
		  position: relative;
			margin-bottom: 172rpx;
			.bg {
			  width: 100%;
			  height: 300rpx;
			  position: absolute;
			  left: 0;
			  top: 0;
			}
			.user-content {
			  position: absolute;
			  z-index: 99;
			  height: 300rpx;
			  display: flex;
			  padding: 0 40rpx;
			  box-sizing: border-box;
				align-items: center;
				.user-avatar {
				  width: 100rpx;
				  height: 100rpx;
				  border-radius: 50%;
					margin-right: 12rpx;
				}
				.user-info {
					.login{
					  font-size: 32rpx;
					  color:#fff;
					}
				}
			}
		}
		.message-container {
			width: 710rpx;
		  height: 142rpx;
		  background-color: #fff;
		  box-sizing: border-box;
		  display: flex;
		  justify-content: space-between;
			align-items: center;
		  position: absolute;
		  top: 280rpx;
		  left: 50%;
		  transform: translateX(-50%);
		  box-shadow:0px 4rpx 52rpx 0px rgba(74,144,226,0.14);
		  border-radius: 8rpx;
		  z-index: 99;
			.item {
				width: 50%;
				text-align: center;
				position: relative;
				font-size: 28rpx;
				&:first-child::after {
					content: '';
					position: absolute;
					width: 2rpx;
					height: 82rpx;
					background-color: #eee;
					top: 50%;
					right: 0;
					transform: translateY(-50%);
				}
				.number {
					color: #353535;
				}
				.name {
					color: #999;
				}
			}
		}
		.common-container {
			margin-bottom: 30rpx;
			.top {
				display: flex;
				justify-content: space-between;
				height: 86rpx;
				align-items: center;
				padding: 0 28rpx;
				background-color: #fff;
				font-size: 32rpx;
				border-bottom: 2rpx solid #e5e5e5;
				.title {
					color: #333;
				}
				.all {
					color: #999;
				}
			}
			.list-conatiner {
				height: 150rpx;
				background-color: #fff;
				display: flex;
				justify-content: space-between;
				align-items: center;
				.item {
					width: 20%;
					text-align: center;
					color: #333;
					font-size: 28rpx;
					image {
						width: 38rpx;
						height: 38rpx;
					}
				}
			}
			.common-list {
				padding: 0 28rpx;
				display: flex;
				flex-wrap: wrap;
				align-items: center;
				background-color: #fff;
				padding-bottom: 20px;
				.item {
					width: 25%;
					text-align: center;
					padding-top: 60rpx;
					color: #333;
					font-size: 28rpx;
					image {
						width: 38rpx;
						height: 38rpx;
					}
				}
			}
		}
	}
</style>
