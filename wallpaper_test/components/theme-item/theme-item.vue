<template>
	<view class="themeItem">
		<navigator url="/pages/classifylist/classifylist" class="box" v-if="!isMore">
			<image class="pic" src="../../common/images/classify1.jpg" mode="aspectFill"></image>
			<view class="mask">
				明星美女
			</view>
			<view class="tab">
				3天前更新
			</view>
		</navigator>
		
		<!-- 更多    此处跳转的页面classify为 tab bar(选项卡栏)  不能像内页一样直接跳转，需要设置open type为relaunch-->
		<navigator url="/pages/classify/classify" open-type="reLaunch" class="box more" v-if="isMore">
			<image class="pic" src="../../common/images/more.jpg" mode="aspectFill"></image>
			<view class="mask">
				<uni-icons type="more-filled" size="30" color="#fff"></uni-icons>
				<view class="text">
					更多
				</view>
			</view>
			

		</navigator>
	</view>
</template>

<script setup>
	
	defineProps({
		isMore:{
			type:Boolean,
			default:false
		}
	})
	
</script>

<style lang="scss" scoped>
	.themeItem{
		
		.box{
			height: 340rpx;
			border-radius: 10rpx;
			overflow: hidden;
			position: relative;
			.pic{
				width: 100%;
				height: 100%;
			}
			.mask{
				width: 100%;
				height: 70rpx;
				position: absolute;
				bottom: 0;
				left: 0;
				background:rgba(0, 0, 0, 0.2);
				color: #fff;
				display: flex;
				align-items: center;
				justify-content: center;
				backdrop-filter:blur(20rpx);//添加磨砂玻璃效果
				font-size: 30;
				font-weight: 600;//字体粗细程度
			}
			.tab{
				position: absolute;
				left: 0;
				top: 0;
				background: rgba(250, 129, 90, 0.7);
				backdrop-filter: blur(20rpx);
				font-size: 22rpx;//网页最小字符大小12px,22rpx=11px，所以这儿字体实际大小是12px，如果还要缩小则可以用transform（使改变，变形。变换）
				color: #fff;
				padding: 6rpx 14rpx;
				border-radius: 0 0 20rpx 0;
				transform: scale(0.8);//transform变形，改变，scale，范围。这里缩放了0.8倍
				transform-origin: left top;//元素变形的原点，这里是以左上为原点变形缩放
			}
		}
		
		//更多专题
		.box.more{
			.mask{
				width: 100%;
				height: 100%;
				flex-direction: column;
				.text{
					font-size: 28rpx;
				}
			}
		}
	}

</style>