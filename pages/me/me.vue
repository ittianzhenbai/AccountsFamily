<template>
	<view>
		<view class="perinfo">
			<view class="info">
				<view class="per-exp">
					个人简介：
				</view>
				<ul class = "info-list">
					<li><text class="text1">姓</text>名：胡歌</li>
					<li><text class="text2">手机</text>号：15038869802</li>
					<li>微信账号：my-one-my621</li>
				</ul>
			</view>
		</view>
		<view class="options">
			<view class="pravite-make">
				我的私人定制
			</view>
			<ul class="items">
				<li class="single-item" v-for="item in 9">
					<view class="pic" v-bind:style="{backgroundImage:'url(' + 'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fc4.haibao.cn%2Fimg%2F400_400_100_0%2F1484189537.9948%2Fc6f9968e90ceec2ddb7fc3eff6e0e385.jpg&refer=http%3A%2F%2Fc4.haibao.cn&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1613615544&t=05d8302aad570ebccea7bfa45a0906ca'+ ')'}"></view>
					<text class="title">个人账单</text>
				</li>
				<li class="single-item" @click="addOption()">
					<view class="pic" v-bind:style="{backgroundImage:'url(' + '../../static/tabar/addAccount.png '+ ')'}"></view>
					<text class="title">添加功能</text>
				</li>
			</ul>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list:[
					{option:"我的亲属关系"},
					{option:"我的打卡记录"},
					{option:"我的目标"},
					{option:"每日动态"},
				]
			};
		},
		onShow(){
			console.log(this.$store.state.test)
		},
		methods:{
			addOption(){
				uni.navigateTo({
					url:"../addOption/addOption"
				})
			}
		}
	}
</script>

<style lang="stylus" scoped>
ul,li
	list-style none
	padding 0
	margin 0
.perinfo
	margin 100rpx 0 0
	width 100%
	height 300rpx
	background-color #FFFFFF
	border-top-left-radius 30rpx
	border-top-right-radius 30rpx
	position relative
	&::before
		content ''
		position absolute
		top -75rpx
		left 50%
		transform translateX(-50%)
		z-index 9
		width 150rpx
		height 150rpx
		border-radius 50%
		border 1px solid #000000
		display inline-block
		background-image url("https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fc4.haibao.cn%2Fimg%2F400_400_100_0%2F1484189537.9948%2Fc6f9968e90ceec2ddb7fc3eff6e0e385.jpg&refer=http%3A%2F%2Fc4.haibao.cn&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1613615544&t=05d8302aad570ebccea7bfa45a0906ca")
		box-shadow 0px 5px 9px 1px rgba(164, 164, 164, 0.51)
		background-size cover
		background-position center center	
	.info
		display inline-block
		vertical-align top
		margin-left 25rpx
		margin-top 80rpx
		.per-exp
			font-family 'Courier New', Courier, monospace
			font-weight bold
		.info-list
			margin-top 20rpx
		.info-list>li
			line-height 50rpx
			font-size 30rpx
			margin-right 30rpx
			color #808080
			.text1
				letter-spacing 60rpx
			.text2
				letter-spacing 15rpx
.options
	width 100%
	height calc(100vh - 406rpx)
	background-color #FFFFFF
	margin-top 6rpx
	overflow auto
	background-image url(http://pic.netbian.com/uploads/allimg/201228/233555-16091697553402.jpg)
	background-size cover
	background-position center center
	.pravite-make
		font-family 'Courier New', Courier, monospace
		font-weight bold
		margin 20rpx 0 30rpx 20rpx
	.items
		margin 0 10rpx 0 20rpx
		.single-item
			display inline-block
			width 100rpx
			text-align center
			margin-right 40rpx
			margin-bottom 30rpx
			.pic
				width 100rpx
				height 100rpx
				background-position center center
				background-size cover
				border-radius 50%
				border 1px solid #808080
			.title
				font-size 22rpx
				color #808080		
</style>
