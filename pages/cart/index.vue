<template>
	<view class="cart-wrapper">
		<view class="tip-contanier">
			<text class="tip">商品库存有限，请尽快下单</text>
			<view class="edit">
				<view @click="onToggleEdit('edit')" v-if="isEdit">完成</view>
				<view @click="onToggleEdit('complete')" v-else>编辑</view>
			</view>
		</view>
		<view class="top-container">
			<icon v-if="isSelectAll" @click="onToggleSelectAll" type="success" size="20" color="#d75843"/>
			<view v-else @click="onToggleSelectAll" class="unselect"></view>
			<text>精选品质生活(全选)</text>
		</view>
		<view class="goods-container">
			<view class="goods-item" v-for="(item, index) in goodsList" :key="index">
				<view class="goods-info">
					<icon v-if="item.isSelect" @click="onToggleSelectItem(index)" type="success" size="20" color="#d75843"/>
					<view v-else @click="onToggleSelectItem(index)" class="unselect"></view>
					<image class="img" :src="item.src" mode="aspectFit"></image>
					<view class="des">
						<view class="name">{{item.name}}</view>
						<view class="introduce">产品：{{item.des}}</view>
					</view>
				</view>
				<view class="price-container">
					<view class="right">
						<view class="price">
							<text class="rmb">￥</text>
							<text>{{item.price}}</text>
						</view>
						<view class="operate">
							<button
								class="buy-num-btn"
								:class="{'btn-minus': item.count === 0}"
								plain='ture'
								@click='onMinusNum(index)'>-</button>
							<text class='buy-num-txt'>{{item.count}}</text>
							<button class="buy-num-btn" plain='ture' @click='onAddNum(index)'>+</button>
						</view>
					</view>
				</view>
			</view>
		</view>
		<view class="recommend-container">
			
		</view>
		<view class="accounts-container">
			<view class="left">
				<icon v-if="isSelectAll" @click="onToggleSelectAll" type="success" size="20" color="#d75843"/>
				<view v-else @click="onToggleSelectAll" class="unselect"></view>
				<text class="select-all">全选</text>
				<text v-if="!isEdit" class="total">总计:￥{{totalMoney}}</text>
			</view>
			<view>
				<view v-if="!isEdit" class="right">去结算</view>
				<view v-else @click="onDelete" class="delete">删除</view>
			</view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			isEdit: false,
			isSelectAll: false,
			goodsList: [
				{
					name: '精选产品名称',
					des: '新鲜营养绿色无污染非转基因食材非转基因食材非转基因食材',
					price: 10.00,
					count: 1,
					isSelect: false,
					src: '../../static/images/cartActive.png',
				},
				{
					name: '精选产品名称',
					des: '新鲜营养绿色无污染非转基因食材非转基因食材非转基因食材',
					price: 5.00,
					count: 4,
					isSelect: false,
					src: '../../static/images/cartActive.png',
				},
				{
					name: '精选产品名称',
					des: '新鲜营养绿色无污染非转基因食材非转基因食材非转基因食材',
					price: 8.00,
					count: 6,
					isSelect: false,
					src: '../../static/images/cartActive.png',
				}
			],
			totalMoney: 0,
		};
	},
	watch: {
		goodsList: {
			handler(list) {
				let totalMoney = 0;
				list.forEach((item) => {
					if(item.isSelect) {
						totalMoney += item.count * item.price
					}
				})
				this.totalMoney = totalMoney;
				const isSelectAll = list.every((item) => {
					return item.isSelect
				})
				if(isSelectAll) {
					this.isSelectAll = true;
				} else {
					this.isSelectAll = false;
				}
			},
			immediate: true,
			deep: true,
		},
	},
	methods: {
		onToggleEdit(type) {
			this.isEdit = !this.isEdit;
		},
		onToggleSelectAll() {
			this.isSelectAll = !this.isSelectAll;
			if(this.isSelectAll) {
				this.goodsList.forEach((item) => {
					item.isSelect = true;
				})
			} else {
				this.goodsList.forEach((item) => {
					item.isSelect = false;
				})
			}
		},
		onToggleSelectItem(index) {
			this.goodsList[index].isSelect = !this.goodsList[index].isSelect;
		},
		onMinusNum(index) {
			if(this.goodsList[index].count > 0) {
				this.goodsList[index].count--;
			} else {
				this.goodsList[index].count = 0;
			}
		},
		onAddNum(index) {
			this.goodsList[index].count++;
		},
		onDelete() {
			const goodsList = this.goodsList.filter((item) => !item.isSelect)
			this.goodsList = goodsList;
		},
	}
};
</script>

<style lang="scss" scoped>
.cart-wrapper {
	width: 100vw;
	min-height: 100vh;
	background-color: #f7f7f7;
	position: relative;
	padding-bottom: 100rpx;
	.unselect {
		width: 40rpx;
		height: 40rpx;
		border: 1px solid #e2e2e2;
		box-sizing: border-box;
		border-radius: 50%;
	}
	.tip-contanier {
		height: 60rpx;
		padding: 0 28rpx;
		display: flex;
		align-items: center;
		justify-content: space-between;
		font-size: 28rpx;
		background-color: red;
		background-color: #fff;
		margin-bottom: 28rpx;
		.tip {
			color: #999999;
		}
		.edit {
			color: #353535;
		}
	}
	.top-container {
		height: 80rpx;
		padding: 0 28rpx;
		display: flex;
		align-items: center;
		border-bottom: 1rpx solid #e2e2e2;
		box-sizing: border-box;
		background-color: #fff;
		text {
			margin-left: 30rpx;
			color: #444;
			font-size: 28rpx;
		}
	}
	.goods-container {
		.goods-item {
			padding: 30rpx 28rpx 30rpx;
			background-color: #fff;
			border-bottom: 1rpx solid #e2e2e2;
			.goods-info {
				display: flex;
				align-items: center;
				.img {
					width: 156rpx;
					height: 156rpx;
					margin: 0 22rpx;
				}
				.des {
					flex: 1;
					display: flex;
					flex-direction: column;
					justify-content: space-between;
					height: 156rpx;
					.name {
						color: #353535;
						font-size: 28rpx;
					}
					.introduce {
						color: #999;
						font-size: 24rpx;
						line-height: 36rpx;
						display: -webkit-box;
						-webkit-box-orient: vertical;
						-webkit-line-clamp: 2;
						overflow: hidden;
					}
				}
			}
			.price-container {
				margin-top: 18rpx;
				display: flex;
				justify-content: flex-end;
				.right {
					height: 60rpx;
					width: 464rpx;
					display: flex;
					justify-content: space-between;
					align-items: center;
					margin-top: 18rpx;
					.price {
						color: #ec645d;
						line-height: 60rpx;
						height: 60rpx;
						display: inline-block;
						.rmb {
							font-size: 28rpx;
						}
					}
					.operate {
						display: flex;
						align-items: center;
						background-color: #f7f7f7;
						.buy-num-btn {
							border: none;
							line-height: 60rpx;
							padding: 0 17rpx;
							color: #999;
						}
						.btn-minus {
							color: #e2e2e2;
						}
						.buy-num-txt {
							width: 88rpx;
							line-height: 60rpx;
							text-align: center;
							color: #353535;
							font-size: 24rpx;
						}
					}
				}
			}
		}
	}
	.accounts-container {
		width: 100vw;
		height: 100rpx;
		border-top: 1rpx solid #e2e2e2;
		position: fixed;
		bottom: 0;
		background-color: #fff;
		display: flex;
		justify-content: space-between;
		align-items: center;
		.left {
			display: flex;
			padding-left: 24rpx;
			.select-all {
				color: #3f3f3f;
				margin-left: 20rpx;
			}
			.total {
				color: #ec554d;
				margin-left: 30rpx;
			}
		}
		.right {
			width: 250rpx;
			height: 100rpx;
			text-align: center;
			background-color: #ec554d;
			line-height: 100rpx;
			color: #fff;
		}
		.delete {
			height: 60rpx;
			width: 136rpx;
			line-height: 60rpx;
			text-align: center;
			box-sizing: border-box;
			border: 1px solid #ec554d;
			margin-right: 28rpx;
			color: #ec554d;
			border-radius: 40rpx;
		}
	}
}
</style>
