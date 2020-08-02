<template>
	<view class="public-wrapper">
		<scroll-view scroll-x class="scroll-container">
			<view class="menu-caontainer">
				<view @click="onChangeMenu(index)" v-for="(item, index) in menuList" :key="index" class="item">
					<view :class="{ 'active': activeIndex === index }">{{item.name}}</view>
				</view>
			</view>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				activeIndex: 0, 
				menuList: [
					{ name: '茶艺' },
					{ name: '中医' },
					{ name: '非转基因' },
					{ name: '支教' },
					{ name: '扶贫' },
					{ name: '传统文化' },
				],
			}
		},
		methods: {
			onChangeMenu(index) {
				this.activeIndex = index;
			},
		}
	}
</script>

<style lang="scss" scoped>
	.public-wrapper {
		.scroll-container {
			border-bottom: 1px solid #eee;
			.menu-caontainer {
				height: 80rpx;
				display: flex;
				display: inline-flex;
				align-items: center;
				padding: 0 28rpx;
				box-sizing: border-box;
				.item {
					color: #131823;
					font-size: 30rpx;
					margin-right: 50rpx;
					word-break: keep-all;
					.active {
						color: #000;
						font-size: 32rpx;
						position: relative;
						&::after {
							content: '';
							width: 100%;
							height: 6rpx;
							background-color: #ec554d;
							position: absolute;
							bottom: -18rpx;
							left: 0;
							border-radius: 3;
						}
					}
				}
			}
		}
	}
</style>
