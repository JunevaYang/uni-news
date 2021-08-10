<template>
	<view class="content">
		<!-- 自定义导航栏 -->
		<navbar></navbar>
		<view v-for="(item, index) in 100" :key="index">
			{{item}} neir
		</view>
	</view>
</template>

<script>
	//easyCom
	//只要组件目录是  components/组件名/组件名.vue 就可以直接使用不需要引用 局部引入
	export default {
		data() {
			return {
				title: 'Hello'
			}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style lang="scss">
	
</style>
