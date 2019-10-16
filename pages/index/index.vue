<template>
	<view class="content">
		
		<view class="text-area">
			<navigator url="../image/image">
			<button plain="true">image</button>
			</navigator>
		</view>
		<view class="text-area">
			<navigator url="../components/button/button">
			<button plain="true">button</button>
			</navigator>
		</view>
		<view class="text-area">
			<navigator url="../vueDemo1/vueDemo1">
			<button plain="true">intersectionObserver</button>
			</navigator>
		</view>
		<view class="text-area">
			<navigator url="../components/recorder/recorder">
			<button plain="true">recorder</button>
			</navigator>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello'
			}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}
	button {
		width: 450upx;
		margin-top: 30upx;
		margin-bottom: 30upx;
		border: 3px solid #B2B2B2;
	}
</style>
