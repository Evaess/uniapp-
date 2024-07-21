<template>
	<view class="homeLayout pageBg">
		<!-- 滚动栏 -->
		<view class="banner">
			<swiper  indicator-dots="true"  indicator-color="#808080" indicator-active-color="#c0c0c0" autoplay="true" circular="true">
				<swiper-item v-for="item in 3">
					<image src="../../common/images/banner1.jpg" mode="aspectFill"></image>
				</swiper-item>
				
			</swiper>
			
		</view>
		<!-- 公共 -->
		<view class="notice">
			<view class="left">
				<uni-icons type="sound-filled" size="20" color="#28b389"></uni-icons>
				<text class="text">公告</text>
			</view>
			<view class="center">
				<swiper vertical="true" autoplay="true" interval="1500" duration="300" circular="true">
					<!-- vertical：是否垂直滑动 autoplay：是否自动轮播 interval：间隔，自动切换时间间隔  duration：持续时间 circular：循环的， -->
					<swiper-item v-for="item in 4">
						文字公告内容
					</swiper-item>
				</swiper>
			</view>
			<view class="right">
				<uni-icons type="right" size="10" color="#333"></uni-icons>
			</view>
			
		</view>
		
		<!-- 选择 -->
		<view class="select">
			<common-title>
				<template #name>
					每日推荐
				</template>
				<template #custom>
					<view class="date">
						<uni-icons type="calendar" size="20" color="#28b389"></uni-icons>
						<view class="text">
							<uni-dateformat :date="Date.now()" format="dd日"></uni-dateformat>
						</view>
						
					</view>
				</template>
			</common-title>
			<view class="content">
				<scroll-view scroll-X="true" >
					<view class="box" v-for="itme in 8">
						<image src="../../common/images/preview_small.webp" mode="aspectFill"></image>
					</view>
				</scroll-view>
			</view>
		</view>
		
		<!-- 主题 -->
		
		<view class="theme">
			<common-title>
				<template #name>
					专题精选
				</template>
				<template #custom>
					<navigator url="" class="more">more+</navigator>
				</template>
			</common-title>
			
			<view class="content">
				<theme-item v-for="item in 8"></theme-item>
				<theme-item :isMore = "true"></theme-item>
			</view>
		</view>
		
	</view>
</template>

<script setup>
	
	
</script>

<style lang="scss" scoped>
.homeLayout{
	
	
	.banner{
		
		width: 750rpx;
		padding: 30rpx 0rpx;
		swiper{
			
			width: 750rpx;
			height: 340rpx;
			&-item{//&-item  =  swiper-item
			
				width: 100%;
				height: 100%;
				padding: 0 30rpx;
				image{
					
					width: 100%;
					height: 100%;
					border-radius: 10rpx;//设置圆角
				}
			}
		}
	}
	.notice{
		width: 690rpx;
		height: 80rpx;
		line-height: 80rpx;
		background-color: #f9f9f9;
		margin: 0 auto;
		border-radius: 80rpx;
		display: flex; //设为块元素,使三个元素水平分布，flex：屈伸伸展
		.left{
			width: 140rpx;
			display: flex;
			align-items: center;
			justify-content: center;
			.text{
				color: $brand-theme-color;
				font-weight: 600;//字体粗细程度
				font-size: 28rpx;
			}
		}
		.center{
			flex: 1;
			swiper{
				width: 100%;
				swiper-item{
					width: 100%;
					font-size: 30rpx;
					color: #666;
					overflow: hidden;//隐藏溢出
					white-space: nowrap;//截断溢出部分并阻止换行
					text-overflow: ellipsis;//溢出部分设置为省略号
				}
			}
		}
		.right{
			width: 70rpx;
			display: flex;
			align-items: center;
			justify-content: center;//display align-items justify-content这三条语句设置完全居中
		}
		
	}
	.select{
		padding-top: 50rpx;
		.date{
			display: flex;
			color: #28b389;
			align-items: center;
			.text{
				margin-left: 5rpx;
			}
		}
		
		.content{
			width: 720rpx;
			margin-left: 30rpx;
			margin-top: 30rpx;
			scroll-view{
				white-space: nowrap;
				.box{
					width: 200rpx;
					height: 430rpx;
					display: inline-block;
					margin-right: 15rpx;
					image{
						width: 100%;
						height: 100%;
						border-radius: 10rpx;
					}
				}
				.box:last-child{margin-right: 30rpx;}
			}
		}
	}
	.theme{
		padding: 50rpx 0;
		.more{
			font-size: 32rpx;
			color: #888;
		}
		.content{
			margin-top: 30rpx;
			padding: 0 30rpx;
			display: grid;
			gap: 15rpx;
			grid-template-columns: repeat(3,1fr);
		}
	}
	
}
</style>
