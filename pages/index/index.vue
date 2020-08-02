<template>
	<view class="index-wrapper">
		<swiper
			indicator-active-color="#fff"
			:indicator-dots="swiperConfig.indicatorDots"
			:autoplay="swiperConfig.autoplay"
			:interval="swiperConfig.interval"
			:duration="swiperConfig.duration"
			:circular="swiperConfig.circular"
			class="swiper">
			<block v-for="(item, index) in swiperConfig.imgUrls" :key="index">
				<swiper-item>
					<image :src="item" class="slide-image" />
				</swiper-item>
			</block>
		</swiper>
		<view class="category-container">
			<view class="item" v-for="(item, index) in categoryList" :key="index">
				<view>
					<image src="../../static/images/categoryActive.png" mode=""></image>
				</view>
				<view class="name">{{item.name}}</view>
			</view>
		</view>
		<view class="spacial-area">
			<view class="title-container">
				<text class="title">会员专享</text>
			</view>
			<scroll-view scroll-x>
				<view class="list-container">
					<view v-for="(item, index) in vipGoodsList" :key="index" class="item">
						<view>
							<image src="../../static/images/bg.png" mode="scaleToFill"></image>
						</view>
						<view class="des">{{item.des}}</view>
						<view class="price">￥{{item.price}}</view>
					</view>
				</view>
			</scroll-view>
		</view>
		<view class="spacial-area">
			<view class="title-container">
				<text class="title">热门推荐</text>
			</view>
			<scroll-view scroll-x>
				<view class="list-container">
					<view v-for="(item, index) in hotGoodsList" :key="index" class="item">
						<view>
							<image src="../../static/images/bg.png" mode="scaleToFill"></image>
						</view>
						<view class="des">{{item.des}}</view>
						<view class="price">￥{{item.price}}</view>
					</view>
				</view>
			</scroll-view>
		</view>
		<view class="discount-area">
			<view class="title-container">
				<text class="title">特惠专区</text>
			</view>
			<scroll-view scroll-x>
				<view class="list-container">
					<view v-for="(item, index) in discountGoodsList" :key="index" class="item">
						<view>
							<image src="../../static/images/bg.png" mode="scaleToFill"></image>
						</view>
						<view class="des">{{item.des}}</view>
						<view class="price">
							<text class="current-price">￥{{item.price}}</text>
							<text class="unit">/{{item.unit}}</text>
							<text class="original-price">￥{{item.originalPrice}}</text>
						</view>
						<view class="sales">
							<text>销量{{item.saleVolume}}笔</text>
							<view class="add">
								<view @click="onAdd(index)" class="iconfont iconadd icon"></view>
								<uni-badge type="success" size="small" :text="item.amount" class="badge">
								</uni-badge>
							</view>
						</view>
					</view>
				</view>
			</scroll-view>
		</view>
	</view>
</template>

<script>
import { uniBadge } from '@dcloudio/uni-ui';

export default {
	components:{
		uniBadge
	},
	data() {
		return {
			swiperConfig : {
				imgUrls: [
					'../../static/images/banner1.png',
					'../../static/images/banner1.png',
					'../../static/images/banner1.png',
				],
				indicatorDots: true,
				autoplay: true,
				interval: 2000,
				duration: 500,
				circular: true,
			},
			categoryList: [
				{ name: '茶叶' },
				{ name: '茶具' },
				{ name: '特产' },
				{ name: '农产品' },
				{ name: '传统文化' },
				{ name: '邀请' },
				{ name: '积分' },
				{ name: '领券' },
				{ name: '会员中心' },
				{ name: '爱心公益' },
			],
			vipGoodsList: [
				{ id: '1', des: '绿色食品实际上是指无污染、安全优质', price: 42.00 },
				{ id: '2', des: '绿色食品实际上是指无污染、安全优质', price: 42.00 },
				{ id: '3', des: '绿色食品实际上是指无污染、安全优质', price: 42.00 },
				{ id: '4', des: '绿色食品实际上是指无污染、安全优质', price: 42.00 },
				{ id: '5', des: '绿色食品实际上是指无污染、安全优质', price: 42.00 },
				{ id: '6', des: '绿色食品实际上是指无污染、安全优质', price: 42.00 },
			],
			hotGoodsList: [
				{ id: '1', des: '绿色食品实际上是指无污染、安全优质', price: 42.00 },
				{ id: '2', des: '绿色食品实际上是指无污染、安全优质', price: 42.00 },
				{ id: '3', des: '绿色食品实际上是指无污染、安全优质', price: 42.00 },
				{ id: '4', des: '绿色食品实际上是指无污染、安全优质', price: 42.00 },
				{ id: '5', des: '绿色食品实际上是指无污染、安全优质', price: 42.00 },
				{ id: '6', des: '绿色食品实际上是指无污染、安全优质', price: 42.00 },
			],
			discountGoodsList: [
				{ id: '1', des: '绿色食品实际上是指无污染、安全优质', unit: '斤', price: 42.00, originalPrice: 64.00, amount: 0, saleVolume: 12 },
				{ id: '2', des: '绿色食品实际上是指无污染、安全优质', unit: '斤', price: 42.00, originalPrice: 64.00, amount: 1, saleVolume: 16 },
				{ id: '3', des: '绿色食品实际上是指无污染、安全优质', unit: '盒', price: 42.00, originalPrice: 64.00, amount: 2, saleVolume: 34 },
				{ id: '4', des: '绿色食品实际上是指无污染、安全优质', unit: '盒', price: 42.00, originalPrice: 64.00, amount: 4, saleVolume: 56 },
				{ id: '5', des: '绿色食品实际上是指无污染、安全优质', unit: '箱', price: 42.00, originalPrice: 64.00, amount: 5, saleVolume: 64 },
				{ id: '6', des: '绿色食品实际上是指无污染、安全优质', unit: '箱', price: 42.00, originalPrice: 64.00, amount: 3, saleVolume: 711 },
			],
		};
	},
	onLoad() {},
	methods: {
		onAdd(index) {
			this.discountGoodsList[index].amount++;
			uni.showToast({
				icon: 'none',
				title: '加入购车成功',
			});
		},
	}
};
</script>

<style lang="scss" scoped>
.index-wrapper {
	background-color: #de5d57;
	position: relative;
	min-height: 100vh;
	padding-bottom: 20rpx;
	.swiper {
		height: 375rpx;
		margin: 0 20rpx 10rpx;
		border-radius: 12rpx;
		overflow: hidden;
		.slide-image {
			width: 100%;
			height: 375rpx;
			border-radius: 12rpx;
		}
	}
	.category-container {
		height: 350rpx;
		margin: 0 20rpx;
		border-radius: 12rpx;
		display: flex;
		flex-wrap: wrap;
		background-color: #fff;
		.item {
			width: 20%;
			height: 175rpx;
			padding: 24rpx 0;
			box-sizing: border-box;
			text-align: center;
			display: flex;
			flex-direction: column;
			justify-content: space-between;
			image {
				width: 76rpx;
				height: 76rpx;
				border-radius: 50%;
			}
			.name {
				color: #404040;
				font-size: 24rpx;
			}
		}
	}
	.spacial-area {
		.title-container {
			height: 92rpx;
			line-height: 92rpx;
			text-align: center;
			.title {
				color: #333;
				font-weight: bold;
				font-size: 32rpx;
				position: relative;
				&::before {
					content: '';
					width: 30rpx;
					height: 2rpx;
					background-color: #aaa9aa;
					position: absolute;
					left: -60rpx;
					top: 50%;
					transform: translateY(-50%);
				}
				&::after {
					content: '';
					width: 30rpx;
					height: 2rpx;
					background-color: #aaa9aa;
					position: absolute;
					right: -60rpx;
					top: 50%;
					transform: translateY(-50%);
				}
			}
		}
		.list-container {
			padding: 0 20rpx;
			display: inline-flex;
			.item {
				width: 180rpx;
				height: 304rpx;
				border-radius: 14rpx;
				font-size: 24rpx;
				margin-right: 20rpx;
				background-color: #fff;
				&:last-child {
					margin-right: 0;
				}
				image {
					width: 180rpx;
					height: 175rpx;
					border-top-left-radius: 14rpx;
					border-top-right-radius: 14rpx;
				}
				.des {
					margin-top: 20rpx;
					margin-bottom: 10rpx;
					padding: 0 20rpx;
					overflow: hidden;
					text-overflow:ellipsis;
					white-space: nowrap;
					color: #424242;
				}
				.price {
					padding: 0 20rpx;
					color: #d75842;
					font-size: 28rpx;
				}
			}
		}
	}
	.discount-area {
		.title-container {
			height: 92rpx;
			line-height: 92rpx;
			text-align: center;
			.title {
				color: #333;
				font-weight: bold;
				font-size: 32rpx;
				position: relative;
				&::before {
					content: '';
					width: 30rpx;
					height: 2rpx;
					background-color: #aaa9aa;
					position: absolute;
					left: -60rpx;
					top: 50%;
					transform: translateY(-50%);
				}
				&::after {
					content: '';
					width: 30rpx;
					height: 2rpx;
					background-color: #aaa9aa;
					position: absolute;
					right: -60rpx;
					top: 50%;
					transform: translateY(-50%);
				}
			}
		}
		.list-container {
			display: flex;
			flex-wrap: wrap;
			padding: 0 20rpx;
			font-size: 24rpx;
			.item {
				width: 350rpx;
				height: 590rpx;
				background-color: #fff;
				border-radius: 16rpx;
				margin-bottom: 10rpx;
				&:nth-child(odd) {
					margin-right: 10rpx;
				}
				image {
					width: 350rpx;
					height: 350rpx;
					border-top-left-radius: 16rpx;
					border-top-right-radius: 16rpx;
				}
				.des {
					margin-top: 20rpx;
					padding: 0 20rpx;
					display: -webkit-box;
					-webkit-box-orient: vertical;
					-webkit-line-clamp: 2;
					overflow: hidden;
					color: #424242;
				}
				.price {
					padding: 20rpx 20rpx;
					color: #d75842;
					.current-price {
						margin-right: 12rpx;
						font-size: 28rpx;
					}
					.unit {
						color: #999;
						margin-right: 12rpx;
					}
					.original-price {
						color: #999;
						text-decoration: line-through;
					}
				}
				.sales {
					padding: 0 20rpx;
					color: #999;
					display: flex;
					justify-content: space-between;
					align-items: center;
					::v-deep .uni-badge--small {
						width: auto !important;
					}
					.add {
						position: relative;
						.icon {
							font-size: 42rpx;
							color: #d75843;
						}
						.badge {
							position: absolute;
							right: -18rpx;
							top: -18rpx;
						}
					}
				}
			}
		}
	}
}
</style>
