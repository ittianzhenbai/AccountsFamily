<template>
	<view class="page">
		<view class="contain">
			<view class="add-detail">
				<ul>
					<li @click = "shouru('1')" :class="item == '1'?'active':''">收入</li>
					<li @click = "zhichu('2')" :class="item == '2'?'active1':''">支出</li>
				</ul>
				<view class="price">
					<text>￥</text>
					<input type="text" value=""  focus="true" v-model="num" readonly/>
				</view>
				<scroll-view 
					scroll-y="true"
					class="scroll-y"
				>
					<view class="items">
						<ul class="item-list">
							<li class="single-item" v-for = "item in 20">
								<image class="pic" src="../../static/images/bj.jpg" mode=""></image>
								<text class="item-name">餐饮</text>
							</li>
						</ul>
					</view>
				</scroll-view>
				<view class="add-beizhu">
					<text class="text1" @click="addbeizhu()">添加备注</text>
					<text class="text2">{{day}}</text>
					<text class="text3">{{riqi}}</text>
				</view>
			</view>
			<view class="keyborder">
				<ul class="keyborder-left">
					<li 
						v-for="(item,index) in keynum" 
						:key="index"
						@click="getMoney(item)"
					>
						{{item}}
					</li>
				</ul>
				<ul class="keyborder-right">
					<li>
						<image 
							class="del-btn" 
							src="../../static/images/del_icon.png" 
							mode=""
							@click="deleteNum()"
						>
						</image>
					</li>
					<li @click="getSure()">确定</li>
				</ul>
			</view>
		</view>
		<view class="alert-beizhu" v-show="isshow == true">
			<view class="alert-box">
				<view class="row1">
					<image @click="closeAlert()" class="colse-btn" src="../../static/images/del.png" mode=""></image>
					<text>请输入备注</text>
					<image @click="saveBeizhu()" class="save-btn" src="../../static/images/save.png" mode=""></image>
				</view>
				<textarea value="" placeholder="请输入0-30字的描述..." />
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				item:"1",
				num:'',
				keynum:["1","2","3","4","5","6","7","8","9","0","."],
				isshow: false
			};
		},
		computed:{
			riqi(){
				let year = new Date().getFullYear()
				let month = new Date().getMonth()+1
				let day = new Date().getDate()
				if(month<9){
					month = `0${month}`
				}
				if(day<11){
					day = `0${day}`
				}
				return `${year}年${month}月${day}日`
			},
			day(){
				let days = new Date().getDay();
				  switch(days) {				
						case 1:				
							  days = '星期一';				
							  break;				
						case 2:				
							  days = '星期二';				
							  break;				
						case 3:				
							  days = '星期三';				
							  break;				
						case 4:				
							  days = '星期四';		
							  break;		
						case 5:	
							  days = '星期五';		
							  break;
						case 6:				
							  days = '星期六';			
							  break;			
						case 0:
							  days = '星期日';
							  break;
				  }
				 return days
			}
		},
		methods:{
			shouru(item){
				this.item = "1"
			},
			zhichu(item){
				this.item = "2"
			},
			getMoney(item){
				this.num +=item
				console.log(item)
			},
			deleteNum(){
				this.num = this.num.substr(0, this.num.length - 1)
			},
			getSure(){
				console.log("在这里会提交你想记录的东西....")
			},
			addbeizhu(){
				this.isshow = true
			},
			closeAlert(){
				this.isshow = false
				console.log("关闭弹窗")
			},
			saveBeizhu(){
				this.isshow = false
				console.log("保存数据")
			}
		}
	}
</script>

<style lang="stylus" scoped>
.contain
	margin 0 10rpx
	.add-detail
		height calc(100vh - 580rpx)
		width 100%
		background-color #FFFFFF
		margin-top 120rpx
		border-top-left-radius 30rpx
		border-top-right-radius 30rpx
		border-bottom-left-radius 10rpx
		border-bottom-right-radius 10rpx
		ul
			margin 10rpx 0 0 20rpx
			&>li
				display inline-block
				width 100rpx
				text-align center
				font-size 16px
				font-family Microsoft YaHei
				font-weight 400
				&.active
					padding-bottom 10rpx
					border-bottom 8rpx solid #000000
				&.active1
					padding-bottom 10rpx
					border-bottom 8rpx solid #D9A525
			&:nth-child(1)
				margin-right 30rpx
		.price
			// margin-top 10px
			margin 10px 20rpx 0
			border-bottom 3rpx solid #C8C7CC
			&>text
				font-size 30px
			&>input
				width 70%
				display inline-block
				height 35px
				font-size 30px
		.scroll-y
			height calc(100vh - 770rpx - 30px)
			.items
				height 600px
				.item-list
					margin 5px 10px 
					.single-item
						// border 2rpx solid red
						margin-bottom 5px
						width 114rpx
						.pic
							border-radius 50%
							display block
							width 80rpx
							height 80rpx
							margin 10rpx auto 5rpx
						.item-name
							font-size 24rpx
							color #808080
							font-family Microsoft YaHei
							font-weight 400
		.add-beizhu
			margin-top 10px
			.text1
				color #61ACFF
				font-size 14px
				margin-left 10px
			.text2,.text3
				float right
			.text2
				margin-left 10px
				margin-right 10px
				color #D9A525
				font-size 14px
				padding-top 2px
	.keyborder
		margin-top 10rpx
		.keyborder-left
			width 75%
			display inline-block
			&>li
				display inline-block
				width 172rpx
				background rgba(250,250,250,0.95)
				margin-right 10rpx
				margin-bottom 10rpx
				height 105rpx
				text-align center
				font-size 48rpx
				line-height 105rpx
				border-radius 10rpx
				&:nth-child(10)
					width 354rpx
					margin-bottom 0
				&:nth-child(11)
					margin-bottom 0
		.keyborder-right
			width 25%
			display inline-block
			vertical-align top
			&>li
				background rgba(250,250,250,0.95)
				border-radius 10rpx
				&:nth-child(1)
					height 105rpx
					margin-bottom 10rpx
					.del-btn
						width 64rpx
						height 64rpx
						position relative
						top 50%
						left 30%
						transform translateX(-50%)
						transform translateY(-50%)
				&:nth-child(2)
					height 335rpx
					text-align center
					line-height 335rpx
					font-size 32rpx
					color #FFFFFF
					font-family Microsoft YaHei
					font-weight Bold
					background rgba(220,193,126,0.9)
.alert-beizhu
	position fixed
	top 0
	height 100%
	width 100%
	width vh
	left 0
	background rgba(000,000,000,0.5)
	z-index 9
	.alert-box
		height calc(100vh - 160rpx)
		width 100%
		margin-top 160rpx 
		background #FFFFFF
		border-top-left-radius 30rpx
		border-top-right-radius 30rpx
		.row1
			padding-top 30rpx
			text-align center
			font-family 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif
			font-weight bold
			.colse-btn,.save-btn
				width 48rpx
				height 48rpx
			.colse-btn
				float left
				width 40rpx
				height 40rpx
				margin-left 30rpx
			.save-btn
				float right
				margin-right 30rpx
		textarea
			height 300rpx
			margin 30rpx 10rpx 0
			border 1px solid #000000
			width calc(100% - 22rpx)
			padding 10rpx
			border-radius 20rpx
				
</style>
