<template>
	<view class="page">
		<map class="map" v-if="status == true" :latitude="latitude" :longitude="longitude"/>
		<text>{{this.latitude}}</text>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				longitude:"",
				latitude:"",
				status:false
			}
		},
		onLoad(){
			this.getWeizhi()
		},
		computed:{
		},
		methods:{
			getWeizhi(){
				let that = this
				uni.chooseLocation({
				    type: 'gcj02',
				    success: function (res) {
						console.log(res)
				        console.log('当前位置的经度：' + res.longitude);
				        console.log('当前位置的纬度：' + res.latitude);
						uni.openLocation({
							latitude: res.latitude,
							longitude: res.longitude,
							success: function () {
								console.log('success');
							}
						});
				    }
				});
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
	.map
		width 100%
		height 50vh
		position fixed
		bottom 0
		left 0
		z-index 99
</style>
