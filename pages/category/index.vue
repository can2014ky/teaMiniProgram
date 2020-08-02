<template>
	<view class="category-wrapper">
		<view class="menu-caontainer">
			<view @click="onChangeMenu(index)" v-for="(item, index) in menuList" :key="index" class="item">
				<view class="">
					<image src="../../static/images/categoryActive.png" mode=""></image>
				</view>
				<view :class="{ 'active': activeMenuIndex === index }">{{item.name}}</view>
			</view>
		</view>
		<view class="main-container">
			<view class="left">
				<view
					@click="onChangeSubMenu(index)"
					v-for="(item, index) in subMenuList"
					:key="index"
					class="item"
					:class="{ 'active': activeSubMenuIndex === index }">
					<view>{{item.name}}</view>
				</view>
			</view>
			<view class="right">
				<view v-for="(item, index) in goodsList" :key="index" class="item">
					<image src="../../static/images/mineActive.png" mode=""></image>
					<view class="content">
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
			</view>
		</view>
	</view>
</template>

<script>
import { uniBadge } from '@dcloudio/uni-ui';

export default {
	components:{
		uniBadge
	},
	data(){
		return {
			activeMenuIndex: 0,
			activeSubMenuIndex: 0,
			menuList: [
				{ name: '茶叶' },
				{ name: '茶具' },
				{ name: '特产' },
				{ name: '农产品' },
				{ name: '传统文化' },
			],
			subMenuList: [
				{ name: '绿茶' },
				{ name: '红茶' },
				{ name: '青茶' },
				{ name: '白茶' },
				{ name: '黄茶' },
				{ name: '黑茶' },
			],
			goodsList: [
				{ id: '1', des: '绿色食品实际上是指无污染、安全优质', unit: '斤', price: 42.00, originalPrice: 64.00, amount: 0, saleVolume: 12 },
				{ id: '2', des: '绿色食品实际上是指无污染、安全优质', unit: '斤', price: 42.00, originalPrice: 64.00, amount: 1, saleVolume: 16 },
				{ id: '3', des: '绿色食品实际上是指无污染、安全优质', unit: '盒', price: 42.00, originalPrice: 64.00, amount: 2, saleVolume: 34 },
				{ id: '4', des: '绿色食品实际上是指无污染、安全优质', unit: '盒', price: 42.00, originalPrice: 64.00, amount: 4, saleVolume: 56 },
				{ id: '5', des: '绿色食品实际上是指无污染、安全优质', unit: '箱', price: 42.00, originalPrice: 64.00, amount: 5, saleVolume: 64 },
				{ id: '6', des: '绿色食品实际上是指无污染、安全优质', unit: '箱', price: 42.00, originalPrice: 64.00, amount: 3, saleVolume: 711 },
			],
		};
	},
	methods: {
		onChangeMenu(index) {
			this.activeMenuIndex = index;
		},
		onChangeSubMenu(index) {
			this.activeSubMenuIndex = index;
		},
		onAdd(index) {
			this.goodsList[index].amount++;
			uni.showToast({
				icon: 'none',
				title: '加入购车成功',
			});
		},
	},
}
</script>

<style lang="scss" scoped>
	.category-wrapper {
		.menu-caontainer {
			height: 160rpx;
			display: flex;
			justify-content: space-between;
			padding: 0 28rpx;
			box-sizing: border-box;
			box-shadow: 0px 6px 6px #fbfbfb;
			.item {
				display: flex;
				flex-direction: column;
				justify-content: space-between;
				text-align: center;
				padding: 16rpx 0;
				color: #59565d;
				font-size: 24rpx;
				image {
					width: 90rpx;
					height: 90rpx;
					border-radius: 50%;
					box-sizing: border-box;
				}
				.active {
					color: #479745;
					font-weight: bold;
				}
			}
		}
		.main-container {
			display: flex;
			margin-top: 6rpx;
			.left {
				width: 160rpx;
				background-color: #f6f6f7;
				color: #595d65;
				font-size: 24rpx;
				min-height: calc(100vh - 166rpx);
				.item {
					height: 100rpx;
					line-height: 100rpx;
					padding-left: 34rpx;
					box-sizing: border-box;
				}
				.active {
					color: #000;
					font-weight: bold;
					background-color: #fff;
				}
			}
			.right {
				flex: 1;
				.item {
					height: 220rpx;
					padding: 20rpx;
					box-sizing: border-box;
					display: flex;
					align-items: center;
					font-size: 24rpx;
					border-bottom: 1rpx solid #eee;
					image {
						width: 160rpx;
						height: 160rpx;
					}
					.content {
						flex: 1;
						padding-left: 20rpx;
						.des {
							display: -webkit-box;
							-webkit-box-orient: vertical;
							-webkit-line-clamp: 2;
							overflow: hidden;
							color: #424242;
						}
						.price {
							padding: 10rpx 0;
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
	}
</style>
