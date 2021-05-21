<template>
	<view class="content">
		<view class="text-area">
			<text class="title">{{title}}月账单</text>
			<scroll-view class="account-list">
				<view class="text1" @click="datapop()">选择日期<text :class="status == false ?'down-icon':'down-icon down-icon-active'"></text></view>
				<view class="account-result" v-show = "status == false">
					<uni-ec-canvas 
						  class="uni-ec-canvas"
						  id="uni-ec-canvas"
						  ref="uni-ec-canvas"
						  canvas-id="uni-ec-canvas"
						  :ec="ec"
						  @inited="inited"
					 ></uni-ec-canvas>
				</view>
				<uni-calendar 
				    :insert="false"
					ref="calendar"
				    :lunar="true" 
				    :startDate="startDate"
				    :endDate="endDate"
					:range="true"
				    @change="change"
					@monthSwitch="monthSwitch"
					@confirm="confirm"
				 ></uni-calendar>
			</scroll-view>
		</view>
	</view>
</template>
<script>
	import ceshi from "@/components/ceshi/ceshi.vue"
	import uniCalendar from '@/components/uni-calendar/uni-calendar.vue'
	import uniEcCanvas from '@/components/uni-ec-canvas/uni-ec-canvas.vue' 
	export default {
		data() {
			return {
				title: '1',
				status:false,
				startDate:"",
				endDate:"",
				msg:"暂时没有获取账单",
				sortItem:['餐饮支出', '购物支出', '礼物支出', '房租支出', '电话费'],
				sortData:[
					{value: 780, name: '餐饮支出'},
					{value: 310, name: '购物支出'},
					{value: 234, name: '礼物支出'},
					{value: 1881, name: '房租支出'},
					{value: 232, name: '电话费'}
				]
			}
		},
		components:{
			ceshi,
			uniCalendar,
			uniEcCanvas
		},
		computed:{
			ec(){
				return {
					option:{
					    title: {
					        text: this.msg,
					        // subtext: '纯属虚构',
					        left: 'center'
					    },
					    tooltip: {
					        trigger: 'item',
					        formatter: '{a} <br/>{b} : {c} ({d}%)'
					    },
					    legend: {
					        orient: 'vertical',
					        left: 'left',
							top: '30',
					        data: this.sortItem
					    },
					    series: [
					        {
					            name: '访问来源',
					            type: 'pie',
					            radius: '55%',
					            center: ['50%', '70%'],
					            data: this.sortData,
					            emphasis: {
					                itemStyle: {
					                    shadowBlur: 10,
					                    shadowOffsetX: 0,
					                    shadowColor: 'rgba(0, 0, 0, 0.5)'
					                }
					            }
					        }
					    ]
					}
				}
			}
		},
		onLoad() {
			
		},
		methods: {
			datapop(){
				this.$refs.calendar.open();
				this.status = true
			},
			confirm(e) {
				console.log(e);
				if(e.range.after == ""){
					this.msg = `${e.fulldate}日的账单`
				}else{
					this.msg = `${e.range.before}到${e.range.after}的账单`
				}
				
				let month = new Date().getMonth()
				this.$nextTick(function(){
					this.status = false
					this.title = month + 1
				})
			},
			monthSwitch(e){
				this.title = e.month
			},
			inited(chart){
				console.log('图表初始化完毕')
				console.log('chart实例', chart)
				
			},
			
		}
	}
</script>

<style lang="stylus" scoped>
.content 
	align-items center
	.text-area 
		text-align center
		margin-top 50rpx
		.title 
			font-size 36rpx
			color #FFFFFF
		.account-list
			height calc(100vh - 98rpx)
			width 100vw
			background-color #FFFFFF
			border-top-left-radius 5%
			border-top-right-radius 5%
			.text1
				text-align left
				padding-left 5%
				font-size 32rpx
				line-height 50px
				border-bottom 1px solid #808080
				.down-icon
					display inline-block
					width 32rpx
					height 32rpx
					background-image url(../../static/images/down_icon.png)
					background-size contain
					background-position center 5rpx
					margin-left 30rpx
				.down-icon-active
					transform rotateX(180deg)
					background-position center -5rpx
			.account-result
				margin-top 20rpx
				.uni-ec-canvas
					display block
					width 100%
					height 600rpx
					margin 0 auto
</style>
