<template>
	<view class="page">
		<view class="search-box" @click="goSearch()">
			<image class="search-icon" src="../../static/images/search-icon.png" mode=""></image>
			<text class="text">请输入你想搜索的关键词</text>
		</view>
		<text>{{msg}}</text>
		<view class="result-list-box">
			<ul class="result-list">
				<li class="single-result">
					<view class="result-content">
						<image class="pic" src="../../static/images/bj.jpg" mode=""></image>
						1.三月到大理赏樱花不远不近
					</view>
				</li>
				<li class="single-result">
					<view class="result-content">
						2.三月到大理赏樱花不远不近,三月到大理赏樱花不远不近
					</view>
				</li>
				<li class="single-result">
					<view class="result-content">
						 3.三月到大理赏樱花不远不近,三月到大理赏樱花不远不近
					</view>
				</li>
				<li class="single-result">
					<view class="result-content">
						4.三月到大理赏樱花不远不近,又近又远
					</view>
				</li>
				<li class="single-result">
					<view class="result-content">
						5.三月到大理赏樱花不远不近,月到大理赏樱花不远不近,又近又远
					</view>
				</li>
				<li class="single-result">
					<view class="result-content">
						6.三月到大理赏樱花不远不近
					</view>
				</li>
			</ul>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				msg:"还未刷新"
			};
		},
		onLoad: function (options) {
			
			this.msg = "开始刷新"
			// setTimeout(function () {
			// 	console.log('start pulldown');
			// }, 1000);
			// uni.startPullDownRefresh();
	   },
		methods:{
			goSearch(){
				uni.navigateTo({
					url:"../search/search"
				})
			},
			onPullDownRefresh() {
				console.log('refresh');
				// this.msg = "刷新成功"
				let _this = this
				setTimeout(function () {
					uni.stopPullDownRefresh();
					_this.$nextTick(function(){
						this.msg = "回到初始状态"
					})
				}, 1000);
			}
		}
	}
</script>

<style lang="stylus">
.page
	width 100%
	height 100vh
	background-color #FFFFFF
	overflow auto
	.search-box
		background-color rgba(245,245,245,0.8)
		height 60rpx
		margin 20rpx 20rpx 40rpx
		width calc(100%-44rpx)
		border-radius 30rpx
		.search-icon
			width 40rpx
			height 40rpx
			float left
			margin 10rpx
		.text
			color #A6A6A6
			line-height 60rpx
	.result-list-box
		// display flex
		// flex-direction row
		.result-list
			column-count 2
			column-gap 0
			// display flex
			// flex-direction column
			.single-result
				box-sizing border-box
				break-inside avoid
				padding 10rpx
				.result-content
					display flex
					flex-direction column
					justify-content center
					align-items center
					padding 20rpx
					height auto
					font-size 36rpx
					color #686868
					box-sizing border-box
					border 1px solid #ccc
					border-radius 20rpx
					.pic
						width calc(100% - 20rpx)
						max-height 200rpx
						border-radius 20rpx
						margin 10rpx
</style>
