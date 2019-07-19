<template>
	<view>
		<paging :total="30" :current='1' :pageSize='3'></paging>
	</view>
</template>

<script>
	import paging from '@/components/uni-yang-fy/fy.vue'
	export default {
		components: {
			paging
		},
		data() {
			return {

			}
		},
	}
</script>

<style>

</style>
