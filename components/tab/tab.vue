<template>
	<view class="tab">
		<scroll-view class="tab-scroll_box">
			<view class="tab-scroll_item" v-for="(item, index) in 10" :key="index">
				{{item}}内容
			</view>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		name:"tab",
		data() {
			return {
				
			};
		}
	}
</script>

<style lang="scss">
	.tab {
		width: 100%;
		.tab-scroll_box {
			width: 100%;
			display: flex;
			flex-direction: row;
		}
	}

</style>
