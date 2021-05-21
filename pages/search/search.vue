<template>
	<view class="page">
		<view class="search-view">
			<view class="search-box" @click="goSearch()">
				<image class="search-icon" src="../../static/images/search-icon.png" mode=""></image>
				<input class="search-keyword" type="text" value="请输入你想搜索的关键词" />
			</view>
			<text class="search-btn">搜索</text>
		</view>
		<view class="key-words">
			<view class="title">热门搜索</view>
			<ul class="keywords-list">
				<li class="single-keywords" v-for="(item,index) in keywords" :key="index">{{item}}</li>
			</ul>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				keywords:[
					"花生豆","毛豆","毛血旺","辣子鸡丁","醋溜豆芽","红烧肉","粉蒸娃娃菜"
				]
			};
		}
	}
</script>

<style lang="stylus" scoped>
.page
	width 100%
	height 100vh
	overflow auto
	background-color #FFFFFF
	.search-view
		width calc(100% - 44rpx)
		margin 20rpx 20rpx 30rpx
		.search-box
			height 60rpx
			background-color rgba(245,245,245,0.8)
			width calc(100% - 100rpx)
			border-top-left-radius 30rpx
			border-bottom-left-radius 30rpx
			display inline-block
			.search-icon
				width 40rpx
				height 40rpx
				float left
				margin 10rpx
			.search-keyword
				color #A6A6A6
				height 60rpx
				line-height 60rpx
		.search-btn
			vertical-align top
			display inline-block
			line-height 60rpx
			width 100rpx
			text-align center
			border-top-right-radius 30rpx
			border-bottom-right-radius 30rpx
			background linear-gradient(to right,#ff9000 0,#ff5000 100%)
	.key-words
		border-top 1px solid #FBFBFB
		.title
			margin 10rpx 0 30rpx 20rpx
		.keywords-list
			margin 0 20rpx
			.single-keywords
				height 56rpx
				display inline-block
				background-color rgba(245,245,245,0.8)
				padding 0 20rpx
				line-height 56rpx
				border-radius 28rpx
				margin-right 20rpx
				margin-bottom 16rpx
</style>
