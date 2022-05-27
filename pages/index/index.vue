<template>
	<view class="content">
		<button @tap="btn">跳转video-list.vue页面</button>
		<button @tap="btn2">跳转video-list2.nvue页面</button>
		<view>以下是引用components里的video-list3.nvue组件，字体是正常的</view>
		<video-list3></video-list3>
	</view>
</template>

<script>
	import VideoList3 from '@/components/video-list3.nvue'
	const ttfUrl = 'https://at.alicdn.com/t/webfont_cmet1sx1z5a.ttf'
	export default {
		components: {
			VideoList3
		},
		data() {
			return {
				title: 'Hello'
			}
		},
		onLoad() {
			// this.loadFontFaceFromCache()
			this.loadFontFaceFromLocal()
		},
		methods: {
			btn() {
				uni.navigateTo({
					url: `/components/video-list`
				});
			},
			btn2() {
				uni.navigateTo({
					url: `/components/video-list2`
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
			// async loadFontFaceFromCache() {
			// 	uni.removeStorageSync('Pacifico')
			//     let tempFilePath
			//     const savedFilePath = uni.getStorageSync('Pacifico')
			//     const [error, res] = await uni.getSavedFileList()
			//     if (!error) {
			//         const fileList = res.fileList
			//         const file = fileList.find(file => file.filePath === savedFilePath)
			//         if (file) {
			//             tempFilePath = file.filePath
			//         }
			//     }
			//     if (!tempFilePath) {
			//         const [error, res] = await uni.downloadFile({
			//             ttfUrl,
			//         })
			//         if (!error) {
			//             tempFilePath = res.tempFilePath
			//             uni.saveFile({
			//                 tempFilePath,
			//                 success(res) {
			//                     uni.setStorage({
			//                         key: 'Pacifico',
			//                         data: res.savedFilePath
			//                     })
			//                 }
			//             })
			//         } else {
			//             console.log('下载失败')
			//             return
			//         }
			//     } else {
			//         console.log('使用缓存资源，跳过下载步骤')
			//     }
			//     uni.loadFontFace({
			//         family: 'font-test',
			//         source: `url("${plus.io.convertLocalFileSystemURL(tempFilePath)}")`
			//     })
			// },
		}
	}
</script>

<style>
	.content {
		font-family: "font-test";
	}
</style>
