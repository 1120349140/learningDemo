<template>
	<view>
		<page-head :title="title"></page-head>
		<view class="uni-padding-wrap uni-common-mt">
			<view class="viewText uni-title uni-common-mt">
				{{appear ? '出现' : '消失'}}
			</view>
			<scroll-view class="scroll-view" scroll-y>
				<view class="scroll-area">
					<text class="notice">向下滚动让头像出现</text>
					<view class="ball">
						<image src="../../static/微信图片_20191015152708.jpg" mode=""></image>
					</view>
				</view>
			</scroll-view>
		</view>
	</view>
</template>
<script>
	let observer = null;
	export default {
		data() {
			return {
				appear: false,
				title: 'intersectionObserver'
			}
		},
		// createIntersectionObserver:创建并返回一个 IntersectionObserver 对象实例。
		// 此处observer == IntersectionObserver
		onReady() {
			
			observer = uni.createIntersectionObserver(this);
			// observer.relativeTo:使用选择器指定一个节点，作为参照区域之一
			// .observer：指定目标节点并开始监听相交状态的变化，回调函数callback包含一个参数result
			observer.relativeTo('.scroll-view').observe('.ball', (res) => {
				// intersectionRatio:observe 回调函数 result 包含的字段,表示相交的比例
				if (res.intersectionRatio > 0 && !this.appear ) {
					this.appear = true;
				} else if (!res.intersectionRatio > 0 && this.appear) {
					this.appear = false;
				}
			})
		},
		onUnload() {
			if (observer) {
				// disconnect:停止监听，回调函数不再触发
				observer.disconnect()
			
			}
		}
	}
</script>
<style>
	.scroll-view {
		height: 400upx;
		background: #fff;
		border: 1px solid #ccc;
		box-sizing: border-box;
	}

	.scroll-area {
		height: 1000upx;
		display: flex;
		flex-direction: column;
		align-items: center;
	}
	.viewText{
		text-align: center;
		font-size:  40upx;
		font-weight: bold;
		margin-bottom: 40upx;
	}

	.notice {
		margin-top: 150upx;
		margin: 150upx 0 400upx 0;
	}

	/* .ball {
		width: 200upx;
		height: 200upx;
		background: #4cd964;
		border-radius: 50%;
	} */
	.ball image {
		width: 300upx;
		height: 350upx;
	}
</style>
