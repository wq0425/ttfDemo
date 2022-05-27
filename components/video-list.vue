<template>
	<view class="content">
		<view>我是video-list.vue：字体正常</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		onLoad() {
			this.loadFontFaceFromLocal()
		},
		methods: {
			listBtn() {
				uni.navigateTo({
					url: `/components/video`
				});
			},
			loadFontFaceFromLocal() {
			    uni.loadFontFace({
			        family: 'font-test',
			        // 本地字体路径需转换为平台绝对路径
			        source: `url(${plus.io.convertLocalFileSystemURL('_www/static/JinTianYunDuoYouDianTian.ttf')})`,
			        success() {
			            console.log('success')
			        },
			        fail(e) {
			            console.log('fail')
			        }
			    })
			},
		}
	}
</script>

<style>
	.content {
		font-family: "font-test";
	}
</style>
