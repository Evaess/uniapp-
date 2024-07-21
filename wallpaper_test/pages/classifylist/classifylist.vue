<template>
	<view class="classifylist">
		<view class="content">
			<navigator url="" v-for="item in 10" class="item">
				<image src="../../common/images/preview2.jpg" mode="aspectFill"></image>
			</navigator>
			
		</view>
		
	</view>
</template>

<script setup>
	
</script>

<style lang="scss" scoped>
	.classifylist{
		.content{
			display: grid;
			grid-template-columns: repeat(3,1fr);
			gap: 5rpx;
			padding: 5rpx;
			.item{
				height: 440rpx;
				image{
					width: 100%;
					height: 100%;
					
					display: block;//将图像转为块元素。防止因图像是行元素而造成图像左右和上下间距不等（行级元素可能包含空格）
					
				}
			}
		}
	}
	
	
	       
</style>
