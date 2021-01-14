
## 前言
简介：首页轮播图，广告轮播图，类似支付宝首页轮播，传入数据即可使用

## 有疑问
微信搜索“慢慢向好”小程序，找客服反馈，相应问题。
				  

## 素材
[图片资源](https://pixabay.com)
 
## 开始使用
下载源码解压，复制`/components` 下的组件至项目根目录的 `/components` 文件夹下


`index.vue`的`script`加入如下部分：
```

import banner from '@/components/ay-banner/banner.vue';
	export default {
		components: {
			banner,

		},
		data() {
			return {
				navbackgroundColor: '#fff',
				themeColor: '#33CCCC',
				"bannerList":  [{
							id: 0,
							img: 'https://cdn.pixabay.com/photo/2016/11/29/13/24/balloons-1869816__340.jpg',
							url: 'www.baidu.com/',
				
						},
						{
							id: 1,
							img: 'https://cdn.pixabay.com/photo/2016/11/23/17/55/beach-1854072__340.jpg',
							url: 'www.baidu.com/',
						},
						{
							id: 2,
							img: 'https://cdn.pixabay.com/photo/2016/11/19/12/25/art-1839006__340.jpg',
							url: 'www.baidu.com/',
						},
					],
				
				"bannerList_two": [{
							id: 0,
							img: 'https://cdn.pixabay.com/photo/2016/11/29/11/57/animal-1869337__340.jpg',
							url: 'www.baidu.com/',
				
						},
						{
							id: 1,
							img: 'https://cdn.pixabay.com/photo/2016/11/21/15/43/beach-1846040__340.jpg',
							url: 'www.baidu.com/',
						},
						{
							id: 2,
							img: 'https://cdn.pixabay.com/photo/2016/11/29/06/20/anniversary-1867767__340.jpg',
							url: 'www.baidu.com/',
						},
					],
			}
		},
		onLoad() {
			let that = this;

		},

		methods: {
			toDetailPage(e) {
				let list = e.list;
				let idx = e.curIndex;
				let list_img = [];
				list.forEach(item => {
					list_img.push(item.img)
				})
				if (list_img && list_img.length > 0) {
					uni.previewImage({
						current: list_img[idx],
						// 传 Number H5端出现不兼容 
						urls: list_img,
						indicator: "number",
						loop: true,
					});
				}
			},

		}
	}
	
```


`index.vue`的`template`加入如下部分：(三选一)
```
 <view >
 	<banner  :list="bannerList" :themeColor="themeColor" @toDetailPage="toDetailPage"></banner>
 	
 	<banner  :list="bannerList_two" @toDetailPage="toDetailPage" :height="200" :padding="20"
 	 :borderRadius="20" :themeColor="themeColor"></banner>
 </view>

```

