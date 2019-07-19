<template>
	<view>
		<view class="fy">
			<view @click="qy(1)">
				首页
			</view>
			<view v-for="value in page" @click="qy(value)" class="">
				{{value}}
			</view>
			<view @click="qy(Number(total/pageSize))">
				尾页
			</view>
		</view>
		<view class="btn-view">
			<view>
				当前页：{{ current }}，数据总量：{{ total }}条，每页数据：{{ pageSize }}
			</view>
		</view>
	</view>
</template>
<script>
	export default {
		name: 'paging',
		props: {
			day: {
				type: Number,
				default: 0
			},
			total: {
				type: Number,
				default: 0
			},
			pageSize: {
				type: Number,
				default: 0
			}
		},
		data() {
			return {
				page: [],
				current: 1
			}
		},
		created: function(e) {
			let that = this
			let total = Number(that.total)
			let pageSize = Number(that.pageSize)
			let zpage = Number(total / pageSize)
			let arr = []
			if (zpage < 5) {
				for (let i = 1; i <= zpage; i++) {
					arr.push(i)
				}
			} else {
				arr = [1, 2, 3, 4, 5]
			}
			that.page = arr
		},
		methods: {
			qy: function(e) {
				let that = this
				that.current = e
				let total = Number(that.total)
				let pageSize = Number(that.pageSize)
				let zpage = Number(total / pageSize)
				let arr = []
				if (zpage < 5) {
					return
				}
				if (e >= zpage - 2) {
					arr = [zpage - 4, zpage - 3, zpage - 2, zpage - 1, zpage]
					that.page = arr
					return
				}
				if (zpage > 5 && e < 4) {
					arr = [1, 2, 3, 4, 5]
					that.page = arr
					return
				}
				if (zpage > 5 && e > 3) {
					arr = [e - 2, e - 1, e, e + 1, e + 2]
					that.page = arr
					return
				}
			}
		},
		onLoad() {

		}
	}
</script>
<style>
	@charset "UTF-8";

	.fy {
		display: inline-block;
		flex-direction: row;
		margin: auto;
		width: 100%;
		margin-top: 50upx;
	}

	.fy view {
		text-align: center;
		display: inline-block;
		width: 80upx;
		height: 80upx;
		line-height: 80upx;
		margin-left: 2%;
		border-radius: 50%;
		background: #00BFFF;
		color: #ffffff;
		font-size: 26upx;
	}

	.fy view:first-child {
		margin-left: 6%;
	}
	.btn-view view{
		text-align: center;
		padding-top: 20upx;
	}
</style>
