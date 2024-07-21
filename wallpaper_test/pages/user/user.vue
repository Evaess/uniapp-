<template>
	<view class="userLayout pageBg">
		<view class="userInfo">
			<view class="avatar">
				<image src="../../static/images/logo2.jpg" mode="aspectFill"></image>
			</view>
			<view class="ip">
				255.255.255
			</view>
			<view class="address">
				来自于：艾利都
			</view>
			
		</view>
		
		<view class="section">
			<view class="list">
				<view class="row" @click="classifList">
					<view class="left">
						<uni-icons type="download-filled" color="#28b389" size="22"></uni-icons>
						<view class="text">
							我的下载
						</view>
					</view>
					
					<view class="right">
						<view class="text">
							33
						</view>
						<uni-icons type="right" size="15" color="#aaa"></uni-icons>
					</view>
				</view>
				
				<view class="row"  @click="classifList">
					<view class="left">
						<uni-icons type="star-filled" color="#28b389" size="22"></uni-icons>
						<view class="text">
							我的评分
						</view>
					</view>
					
					<view class="right">
						<view class="text">
							33
						</view>
						<uni-icons type="right" size="15" color="#aaa"></uni-icons>
					</view>
				</view>
				
				<view class="row" >
					<view class="left">
						<uni-icons type="chat-filled" color="#28b389" size="22"></uni-icons>
						<view class="text">
							联系客服
						</view>
						
						<!-- 条件编译用于做多端适配 1仅微信小程序触发，2，h5和app可触发-->
						<!-- #ifdef MP-WEIXIN -->
						<button open-type="contact">联系微信客服</button>
						<!-- #endif -->
						
						<!-- #ifdef H5||APP -->
						<button @click="clickContact">联系微信客服</button>
						<!-- #endif -->
					</view>
					
					<view class="right">
						<view class="text">
							33
						</view>
						<uni-icons type="right" size="15" color="#aaa"></uni-icons>
					</view>
				</view>
				
				
			</view>
		</view>
		
		<!-- //下方栏 -->
		<view class="section">
			<view class="list">
				<view class="row" >
					<view class="left">
						<uni-icons type="notification-filled" color="#28b389" size="22"></uni-icons>
						<view class="text">
							订阅更新
						</view>
					</view>
					
					<view class="right">
						<view class="text">
							33
						</view>
						<uni-icons type="right" size="15" color="#aaa"></uni-icons>
					</view>
				</view>
				
				<view class="row" >
					<view class="left">
						<uni-icons type="flag-filled" color="#28b389" size="22"></uni-icons>
						<view class="text">
							常见问题
						</view>
					</view>
					
					<view class="right">
						<view class="text">
							33
						</view>
						<uni-icons type="right" size="15" color="#aaa"></uni-icons>
					</view>
				</view>
				
				
			</view>
		</view>
		
	</view>
</template>

<script setup>
	const clickContact =()=>{
		uni.makePhoneCall({
			phoneNumber: '1008611' //仅为示例
		});

	}
	
	const classifList =()=>{
		//在起始页面跳转到test.vue页面并传递参数 
		uni.navigateTo({
			url: "/pages/classifylist/classifylist"
		});

	}
	
</script>

<style lang="scss" scoped>
	.userLayout{
		.userInfo{
			display: flex;
			align-items: center;
			justify-content: center;
			flex-direction: column;
			padding: 50rpx 0;
			.avatar{
				width: 160rpx;
				height: 160rpx;
				border-radius: 50%;
				overflow: hidden;//超出部分隐藏
				image{
					width: 100%;
					height: 100%;
				}
				
			}
			.ip{
				font-size: 44rpx;
				color: #333;
				padding: 20rpx 0 5rpx;
			}
			.address{
				font-size: 28rpx;
				color: #aaa;
			}
			
		}
		
		.section{
			width: 690rpx;
			margin: 50rpx auto;
			border: 1rpx solid #eee;
			border-radius: 10rpx;
			box-shadow: 0 0 30rpx rgba(0, 0, 0, 0.05);
			
			.list{
				
				.row{
					background-color: #fff;
					position: relative;
					display: flex;
					justify-content: space-between;
					align-items: center;
					padding: 0 30rpx;
					height: 100rpx;
					border-bottom: 1rpx solid #eee;
					&:last-child{border-bottom: 0;}
					.left{
						display: flex;
						align-items: center;
						.text{
							padding-left: 20rpx;
							color: #666;
						}
					}
					.right{
						display: flex;
						align-items: center;
						.text{
							font-size: 28rpx;
							color:#aaa;
						}
					}
					button{
						position: absolute;
						left: 0;
						top: 0;
						width: 100%;
						height: 100%;
						opacity: 0;//透明度
					}
				}
			}
			
		}
	}
	       
</style>
