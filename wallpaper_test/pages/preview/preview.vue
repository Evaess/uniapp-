<template>
	<view class="preview">
		<swiper circular="true" :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
			<swiper-item v-for="item in 5">
				<image @click="maskChange" src="../../common/images/preview1.jpg" mode="aspectFill"></image>
			</swiper-item>
		</swiper>
		
		
		<view class="mask" v-if="maskState">
			<view class="goBack">
				
			</view>
			<view class="count">
				3 / 9
			</view>
			<view class="time">
				<uni-dateformat :date="new Date()" format="hh:mm"></uni-dateformat>
			</view>
			<view class="date">
				<uni-dateformat :date="new Date()" format="MM月dd日"></uni-dateformat>
			</view>
			<view class="footer">
				<view class="box" @click="clickInfo">
					<uni-icons type="info" size="28"></uni-icons>
					<view class="text">
						信息
					</view>
				</view>
				
				<view class="box">
					<uni-icons type="star" size="28"></uni-icons>
					<view class="text">
						2分
					</view>
				</view>
				
				<view class="box">
					<uni-icons type="download" size="25"></uni-icons>
					<view class="text">
						下载
					</view>
				</view>
				
			</view>
		</view>
		<uni-popup ref="infoPopup" type="bottom">
		<view class="infoPopup">
			<!-- 弹窗头部 -->
			<view class="popupHeader">
				<view class="">
					<!-- 空盒子方便头部三等分布局 -->
				</view>
				<view class="title">
					壁纸信息
				</view>
				<view class="close" @click="clickInfoClose">
					<uni-icons type="closeempty" size=""></uni-icons>
				</view>
			</view>
			<!-- 弹窗内容 -->
			<scroll-view scroll-y="true" class="scroll" >
				<view class="content">
					<view class="row" >
						<view class="labe">
							壁纸id:
						</view>
						<text selectable="trues" class="value">1223123213</text>
					</view>
					
					<view class="row" >
						<view class="labe">
							分类:
						</view>
						<text selectable="trues" class="value class">明星美女</text>
					</view>
					
					<view class="row" >
						<view class="labe">
							发布者:
						</view>
						<text selectable="trues" class="value">张三</text>
					</view>
					
					<view class="row" >
						<view class="labe">
							评分:
						</view>
						<view  class="value roteBox">
							<uni-rate v-model="value" @change="onChange" readonly/>
							<text class="score">4分</text>
						</view>
					</view>
					
					<view class="row">
						<view class="labe">
							摘要:
						</view>
						<text selectable="trues" class="value">摘要文字填充摘要文字填充摘要文字填充摘要文字填充摘要文字填充
						摘要文字填充摘要文字填充摘要文字填充摘要文字填充摘要文字填充摘要文字填充摘要文字填充摘要文字填充</text>
					</view>
					
					<view class="row">
						<view class="labe">
							标签:
						</view>
						<view class="value tabs">
							<view class="tab" v-for="item in 3">
								标签名
							</view>
						</view>
					</view>
					
					<!-- 版权申明 -->
					<view class="copyright">
						以上图片均来自网络，侵权必删。
					</view>
					
				</view>
			</scroll-view>
			
		</view>
		</uni-popup>
		
	</view>
</template>

<script setup>
import { ref } from 'vue';
	
	const maskState = ref(true);//遮罩层状态
	const infoPopup = ref(null);
	
	//点击关闭弹窗（弹窗右上角X）
	const clickInfoClose = ()=>{
		infoPopup.value.close();
	}
	
	//点击开启弹窗
	const clickInfo = ()=>{
		infoPopup.value.open();
	}
	
	//遮罩层显隐
	const maskChange = ()=>{
		maskState.value = !maskState.value;
	}
	
</script>

<style lang="scss" scoped>
	.preview{
		width: 100%;
		height: 100vh;
		position: relative;
		swiper{
			width: 100%;
			height: 100%;
			image{
				width: 100%;
				height: 100%;
			}
		}
		
		//遮罩层布局
		.mask{
			&>view{//&父级 >表相邻子元素
			position: absolute;
			left: 0;
			right: 0;
			margin: auto;//左右0 边缘自动可使得元素自动居中
			width: fit-content; //宽度为包裹内容
			color: #fff;
			}
			.goBack{
				
			}
			.count{
				
				top: 10vh;
				
				background: rgba(0, 0, 0, 0.3);
				font-size: 28;
				
				border-radius: 40rpx;
				padding: 8rpx 28rpx;
				backdrop-filter: blur(10rpx);
				
			}
			.time{
				
				font-size: 140rpx;
				top: calc(10vh + 80rpx);
				font-weight: 100;
				line-height: 1em;
				text-shadow: 0 4rpx rgba(0, 0, 0, 0.3);
				
			}
			.date{
				font-size: 34rpx;
				top: calc(10vh + 230rpx);
				text-shadow: 0 2rpx rgba(0, 0, 0, 0.3);
				
			}
			.footer{
				background-color: rgba(255, 255, 255, 0.8);
				bottom: 10vh;
				width: 65vw;
				height: 120rpx;
				border-radius: 120rpx;
				display: flex;
				justify-content: space-around;
				align-items: center;
				color: #000;
				box-shadow: 0 2rpx rgba(0, 0, 0, 0.1);
				backdrop-filter: blur(20rpx);//模糊
				.box{
					display: flex;
					flex-direction: column;
					align-items: center;
					justify-content: center;
					padding: 2rpx 12rpx;
					.text{
						font-size: 26rpx;
						color: $text-font-color0-2;
					}
				}
				
			}
		}
		
		//弹窗布局
		.infoPopup{
			background-color: #fff;
			padding: 30rpx;
			border-radius: 50rpx 50rpx 0 0; 
			overflow: hidden;
				
			.popupHeader{
				display: flex;
				flex-direction: row;
				align-items: center;
				justify-content: space-between;
				
				.title{
					color: $text-font-color0-2;
				}
				
				.close{
					padding: 3rpx;
				}
			}
			.scroll{
				max-height: 60vh;
				
				.content{
					.row{
						display: flex;
						
						
						
						padding: 16rpx 0;
						font-size: 32rpx;
						line-height: 1.7em;
						
						.labe{
							font-size: 30rpx;
							color: $text-font-color0-3;
							width: 140rpx;
							text-align: right;
							padding-right: 15rpx;
						}
						.value{
							flex: 1;
							width: 0;
						}
						.roteBox{
							display: flex;
							align-items: center;
							
							.score{
								margin-left: 10rpx;
							}
						}
						
						.tabs{
							display: flex;
							align-items: center;
							flex-wrap: wrap; //自动换行
							.tab{
								border: 1rpx solid $brand-theme-color;
								color: $brand-theme-color;
								font-size: 22rpx;
								padding: 10rpx 30rpx;
								border-radius: 40rpx;
								line-height: 1em;
								margin: 0 10rpx 10rpx 0;
								
							}
						}
						
						.class{
							color: $brand-theme-color;
						}
					}
					
					//版权申明
					.copyright{
						font-size: 28rpx;
						padding: 22rpx;
						background: #f6f6f6;
						color: #666;
						border-radius: 10rpx;
						margin: 20rpx 0;
						line-height: 1.5em;
					}
					
				}
			}
				
			
			
		}
	}
	
		   
</style>
