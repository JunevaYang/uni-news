<template>
	<view class="navbar">
		<view class="navbar-fixed">
			<!-- 处理状态栏高度 -->
			<view :style="{height: statusBarHeight + 'px;'}"></view>
			<!-- 导航栏内容 -->
			<view class="navbar-content" :style="{height:navBarHeight+'px',width:windowWidth+'px'}">
				<view class="navbar-serach">
					<view class="navbar-serach_icon">
						<uni-icons type="search" size="16" color="#999"></uni-icons>
					</view>
					<view class="navbar-serach_text"></view>
				</view>
			</view>
		</view>
		<view :style="{height:statusBarHeight+navBarHeight+'px'}"></view>
	</view>
</template>

<script>
	export default {
		name: "navbar",
		data() {
			return {
				statusBarHeight: 20,
				navBarHeight: 45,
				windowWidth: 375,
			};
		},
		created() {
			//获取手机系统信息
			const info = uni.getSystemInfoSync()
			console.log(info)
			this.statusBarHeight = info.statusBarHeight
			this.windowWidth = info.windowWidth

			// #ifndef H5 || APP-PLUS ||MP-ALIPAY
			//获取小程序胶囊位置
			const menuButtonInfo = uni.getMenuButtonBoundingClientRect()
			console.log(menuButtonInfo)
			// (胶囊底部高度 - 状态栏的高度) + (胶囊顶部高度 - 状态栏内的高度) = 导航栏的高度
			this.navBarHeight = (menuButtonInfo.bottom - info.statusBarHeight) + (menuButtonInfo.top - info
				.statusBarHeight)
			this.windowWidth = menuButtonInfo.left
			// #endif
			console.log(this.statusBarHeight+this.navBarHeight)
		}
	}
</script>

<style lang="scss">
	.navbar {
		.navbar-fixed {
			position: fixed;
			top: 0;
			left: 0;
			z-index: 99;
			width: 100%;
			background-color: $mk-base-color;

			.navbar-content {
				height: 45px;
				padding: 0 15px;
				display: flex;
				justify-content: center;
				align-items: center;
				box-sizing: border-box;

				.navbar-serach {
					display: flex;
					align-items: center;
					padding: 0 10px; 
					width: 100%;
					height: 30px;
					border-radius: 30px;
					background-color: #FFFFFF;

					.navbar-serach_icon {
						margin-right: 10px;
					}

					.navbar-serach_text {
						font-size: 12px;
						color: #999;
					}
				}
			}
		}
	}
</style>
