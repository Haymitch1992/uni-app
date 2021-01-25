<template>
	<view class="container">
		<view class="search-constainer">
			<view class="head-box">
				<view class="flex-item">
					<text class="flex-title" :class="currentTab===0?'active':''" @click="currentTab=0">查公司</text>
				</view>
				<view class="flex-item">
					<text class="flex-title"  :class="currentTab===1?'active':''" @click="currentTab=1">查老板</text>
				</view>
				<view class="flex-item">
					<text class="flex-title"  :class="currentTab===2?'active':''" @click="currentTab=2">查关系</text>
				</view>
			</view>
			<view class="search-box">
				<input class="uni-input search-input" focus :placeholder="inputPlaceholder[currentTab]" />
			</view>
			<view class="hot-search">
				<image class="hot-icon" src="../../static/hotkey-icon-2.png" mode=""></image>
				<text class="hot-text">|</text>
				<text class="hot-text" :key="index" v-for="(item,index) in hotWord[currentTab]">{{item}}</text>
			</view>
		</view>
		<page-footer></page-footer>
	</view>
</template>

<script>
	import pageFooter from '../../components/footer/footer.vue'
	export default {
		data() {
			return {
				href: 'https://uniapp.dcloud.io/component/README?id=uniui',
				currentTab:0,
				inputPlaceholder:[
					'输入公司名称、老板姓名、品牌名称等',
					'输入老板信息，如‘马云 杭州’',
					'输入公司名称或老板姓名'
				],
				hotWord:[
					['恒大汽车','网易','恒大汽车','网易','恒大汽车','网易'],
					['马云','王思聪','马云','王思聪','马云','王思聪',],
					['饿了吗-阿里','美团-摩拜','饿了吗-阿里','美团-摩拜',]
				]
			}
		},
		components:{
			pageFooter
		},
		methods: {

		}
	}
</script>

<style lang="scss">
	.container {
		font-size: 14px;
	}
	.search-constainer{
		padding-top: 106px;
		background-color: #0084ff;
		background-image: url("../../static/mainbglogo-2.png");
		min-height: 232px;
		background-position: center;
		background-size: cover;
		box-sizing: border-box;
		.head-box{
			color: #fff;
			display: flex;
			padding: 0 60rpx;
			    flex-direction: row;
				.flex-title{
					position: relative;
					font-size: 30rpx;
					color: rgba(255, 255, 255, 0.6);
				}
				.active{
					color: #fff;
				}
			.active:after{
				content: '';
				position: absolute;
				height: 2px;
				width: 24px;
				background: #fff;
				top: 25px;
				left: calc(50% - 12px);
				border-radius: 2px;
			}
			.flex-item {
				width: 33.3%;
				height: 60rpx;
				text-align: center;
				line-height: 60rpx;
			}
		}
		.search-box{
			padding: 26rpx 20rpx 0;
		}
		.search-input{
			width: 100%;
			height: 42px;
			border: none;
			border-radius: 4px;
			color: #454545;
			background-color: #fff;
			padding: 0 14px;
			box-sizing: border-box;
			font-size: 14px;
		}
		.hot-icon{
			width: 50rpx;
			height: 24rpx;
		}
		.hot-search{
			padding: 10px 20rpx 0;
			color: #fff;
			.hot-text{
				margin: 0 6rpx;
				font-size: 22rpx;
			}
		}
	}
</style>
