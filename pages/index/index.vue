<template>
	<view class="content" :style="{width: screenWidth+ 'px'}" v-if="showBorder">
		<view class="header">
			<view class="logo">
				<image src="/static/baike.png" mode="widthFix"></image>
			</view>
			<view style="margin-top: 10px;" @click="refesh()"> {{datetime}}
				</view>

					<!-- <button @click="sss()">dianji</button> -->
			</view>
			<view class="bodyBorder">
				<view class="uni-margin-wrap">
					<swiper class="swiper" circular :indicator-dots="indicatorDots" :autoplay="autoplay"
						:interval="interval" :duration="duration">
						<swiper-item>

							<view class="Border-header"
								style="width: 100%;font-size: 28px;font-weight: 800;text-align: center;">
								加&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;工&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;计&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;划&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;明&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;细&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;表

							</view>
							<view class="title-list">
								<view class="header-list" style="display: flex;flex-direction: row;width: 100%;">
									<view class="base-text1"
										style="width: 15%;text-align: center;font-weight:bold;font-size:18px;">制令单号
									</view>
									<view class="base-text1"
										style="width: 10%;text-align: center;font-weight:bold;font-size:18px;">工单</view>
									<view class="base-text1"
										style="width: 15%;text-align: center;font-weight:bold;font-size:18px;">物料</view>
									<view class="base-text1"
										style="width: 10%;text-align: center;font-weight:bold;font-size:18px;">类别</view>
									<view class="base-text1"
										style="width: 30%;text-align: center;font-weight:bold;font-size:18px;">半成品描述
									</view>
									<view class="base-text1"
										style="width: 5%;text-align: center;font-weight:bold;font-size:18px;">数量</view>
									<view class="base-text1"
										style="width: 12.5%;text-align: center;font-weight:bold;font-size:18px;">计划完成
									</view>
									<view class="base-text1"
										style="width: 12.5%;text-align: center;font-weight:bold;font-size:18px;">实际完成
									</view>
								</view>
							</view>
							<view class="list-scall">
								<base-scroll-list :rowsDataProps="record2"></base-scroll-list>
							</view>
						</swiper-item>



						<swiper-item>
							<view class="Border-header"
								style="width: 100%;font-size: 28px;font-weight: 800;text-align: center;">
								加&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;工&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;任&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;务&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;工&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;作&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;安&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;排&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;表

							</view>
							<view class="title-list">
								<view class="header-list" style="display: flex;flex-direction: row;width: 100%;">
									<view class="base-text1"
										style="width: 12.5%;text-align: center;font-weight:bold;font-size:18px;">制令单号
									</view>
									<view class="base-text1"
										style="width:7.5%;text-align: center;font-weight:bold;font-size:18px;">机床名称
									</view>
									<view class="base-text1"
										style="width: 7.5%;text-align: center;font-weight:bold;font-size:18px;">工单号
									</view>
									<view class="base-text1"
										style="width: 10%;text-align: center;font-weight:bold;font-size:18px;">物料编码
									</view>
									<view class="base-text1"
										style="width: 30%;text-align: center;font-weight:bold;font-size:18px;">物料描述
									</view>
									<view class="base-text1"
										style="width:10%;text-align: center;font-weight:bold;font-size:18px;">排产件数
									</view>
									<view class="base-text1"
										style="width: 15%;text-align: center;font-weight:bold;font-size:18px;">单件标准工序工时
									</view>
									<view class="base-text1"
										style="width:7.5%;text-align: center;font-weight:bold;font-size:18px;">操作员
									</view>
								</view>
							</view>
							<view class="list-scall">
								<ScrollList :rowsDataProps="record3"></ScrollList>
							</view>

						</swiper-item>






						<swiper-item>
							<view class="swiper-item">
								<view class="body-border" style="margin-top:20px">
									<view class="left-border">
										<view class="CountryGif">
											<view class="gif_img">

											</view>
											<!-- <image :src="gifFile"></image> -->

										</view>
										<view class="chart1">
											<echarts :option="option" class="echartsBorder"></echarts>
										</view>

									</view>

									<view class="right-border">
										<view class="Border-header"
											style="width: 100%;font-size: 28px;font-weight: 800;text-align: center;">
											加&nbsp;&nbsp;&nbsp;工&nbsp;&nbsp;&nbsp;任&nbsp;&nbsp;&nbsp;务&nbsp;&nbsp;&nbsp;达&nbsp;&nbsp;&nbsp;成&nbsp;&nbsp;&nbsp;率&nbsp;&nbsp;&nbsp;汇&nbsp;&nbsp;&nbsp;总&nbsp;&nbsp;&nbsp;表

										</view>
										<view class="title-list">
											<view class="header-list"
												style="display: flex;flex-direction: row;width: 100%;">
												<view class="base-text1"
													style="width: 15%;text-align: center;font-weight:bold;font-size:18px;">
													操作员</view>
												<view class="base-text1"
													style="width: 20%;text-align: center;font-weight:bold;font-size:18px;">
													日期</view>
												<view class="base-text1"
													style="width:20%;text-align: center;font-weight:bold;font-size:18px;">
													工作类别</view>
												<view class="base-text1"
													style="width: 15%;text-align: center;font-weight:bold;font-size:18px;">
													工作总工时</view>
												<view class="base-text1"
													style="width: 20%;text-align: center;font-weight:bold;font-size:18px;">
													完成标准工时</view>
												<view class="base-text1"
													style="width: 10%;text-align: center;font-weight:bold;font-size:18px;">
													达成率</view>
												<!-- 	<view class="base-text1" style="width: 10%;text-align: center;font-weight:bold;font-size:18px;">备注</view> -->

											</view>
										</view>

										<OutScrollList :rowsDataProps="record4"></OutScrollList>
									</view>
								</view>

							</view>
						</swiper-item>
					</swiper>
				</view>

			</view>
		</view>
</template>

<script>
	import echarts from '@/components/echarts/echarts.vue'
	import maoScroll from '@/components/mao-scroll/mao-scroll.vue';
	import baseScrollList from './com/baseScrollList.vue';
	import ScrollList from './com/ScrollList.vue'
	import OutScrollList from './com/OutScrollList.vue'

	export default {
		components: {
			maoScroll,
			baseScrollList,
			ScrollList,
			OutScrollList
		},
		data() {
			return {
				showBorder: true,
				datetime: '',
				option: {},
				title: 'Hello',
				indicatorDots: false,
				autoplay: true,
				interval: 50000,
				duration: 500,
				//滚动表单
				record: [],
				record2: [],
				record3: [],
				record4: [],
				record5: [],
				data: [],
				count: 100,
				showNum: 8,
				lineHeight: 120,
				animationScroll: 1500,
				animation: 2000,
				gifFile: '/static/2.gif',
				screenWidth: uni.getSystemInfoSync().screenWidth // 获取当前设备的屏幕宽度

			}
		},
		onLoad() {
			// this.Getapi()
			this.Getapi2()

			this.Getapi3()
			this.Getapi4()
			this.Getapi5()
			this.showtime()
			this.Showtimeout()

		},
		methods: {


			Showtimeout() {
				console.log('循环')

				setInterval(() => {

					this.$nextTick(() => {
						this.showBorder = true
						this.Getapi2()
						this.Getapi3()
						this.Getapi4()
						this.Getapi5()
					})

				}, 10000)

			},
			refesh() {


				console.log('刷新')
				this.showBorder = false
				this.$nextTick(() => {
					this.showBorder = true
					this.Getapi2()
					this.Getapi3()
					this.Getapi4()
					this.Getapi5()
				})


			},
			scroll() {
				this.animate = true;
				setTimeout(() => {
					this.notics.push(this.notics[0]);
					this.notics.shift();
					this.animate = false;
				}, 1000);
			},
			
			Getapi2() {
				uni.request({
					method: 'post',
					url: 'http://192.168.110.236:809/KBAPI/GetKBManPlan?sDept=机加工',
					headers: {
						'Content-Type': 'Content-Type'
					},
				}).then(res => {
					this.record2 = JSON.parse(res.data)
					console.log(this.record2, '明细表record2')
				}).catch(err => {
					console.log(err)
				})
			},
			Getapi3() {
				uni.request({
					method: 'get',
					url: 'http://192.168.110.236:809/KBAPI/Get_KBDayPlan?sDept=机加工',
					headers: {
						'Content-Type': 'Content-Type'
					},
				}).then(res => {
					this.record3 = JSON.parse(res.data)
					console.log(this.record3, '日计划record3')
				}).catch(err => {
					console.log(err)
				})
			},
			Getapi4() {
				uni.request({
					method: 'post',
					url: 'http://192.168.110.236:809/KBAPI/Get_KBOutPlan?sDept=机加工',
					headers: {
						'Content-Type': 'Content-Type'
					},
				}).then(res => {
					this.record4 = JSON.parse(res.data)
					console.log(this.record4, '工作完成情况')
				}).catch(err => {
					console.log(err)
				})
			},
			Getapi5() {
				// uni.request({
				// 	method: 'post',
				// 	url: 'http://192.168.110.236:809/KBAPI/Get_KBManPlanQtySum',

				// 	headers: {
				// 		'Content-Type': 'Content-Type'
				// 	},
				// }).then(res => {
				// 	this.record5 = JSON.parse(res.data)
				// 	console.log(this.record5,'a55555')
				// 	console.log(this.record5.length,'55555')
				// 	this.record5 = this.record5.map(item=>{return {name:item.CompleteState,value:item.qty}});
				// 	console.log(this.record5,'resthis.record5')
				// 	this.logstatrt()
				// }).catch(err => {
				// 	console.log(err)
				// })
			},
			logstatrt() {
				this.option = {
					color: [

						'rgb(118, 218, 145)',
						'rgb(248, 203, 127)',
						'rgb(248,149,163)',
						'#aaaaff',
						'#ffaaff',
					],
					title: {
						text: '订单按时完成状态',
						left: 'center',
						textStyle: {
							color: '#ffffff',
							fontSize: '16'
						},
					},
					tooltip: {
						trigger: 'item'
					},
					legend: {
						bottom: 30,
						left: 'center',
						textStyle: {
							color: '#ffffff',
						},
					},
					series: [{
						name: '数量',
						type: 'pie',
						radius: '50%',
						center: ['50%', '50%'],
						label: {
							show: true,
							position: 'inner',
							formatter: '{d}%',
							textStyle: {
								color: '#ffffff',
							},
						},
						data: this.record5,
						emphasis: {
							itemStyle: {
								shadowBlur: 10,
								shadowOffsetX: 0,
								shadowColor: 'rgba(0, 0, 0, 0.5)'
							}
						}
					}]
				};
			},
			showtime() {
				var datetime = new Date()
				var year = datetime.getFullYear();
				var day = datetime.getDay();
				var weeks = new Array(
					"星期日",
					"星期一",
					"星期二",
					"星期三",
					"星期四",
					"星期五",
					"星期六"
				);
				var week = weeks[day];
				var month = datetime.getMonth() + 1; //js从0开始取
				var date = datetime.getDate();
				var hour = datetime.getHours();
				var m = datetime.getMinutes();
				var s = datetime.getSeconds();
				month = month < 10 ? "0" + month : month;
				date = date < 10 ? "0" + date : date;
				hour = hour < 10 ? "0" + hour : hour;
				m = m < 10 ? "0" + m : m;
				s = s < 10 ? "0" + s : s;
				this.datetime = year + "-" + month + "-" + date + " " + week
				console.log(this.datetime, 'this.datetime')
				return year + "-" + month + "-" + date;
				return week;

			},
		},



	}
</script>

<style>
	page {
		background: url(/static/14.png);
		background-size: cover;
		background-repeat: no-repeat;
		height: 100vh;
		/* width:1100px; */
		/* 1920:1080 */
		color: white;
	}

	.content {
		display: flex;
		flex-direction: column;
		height: 100%;

	}

	.header {
		height: 6%;
		width: 98%;
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		margin-bottom: 1%;
	}

	.logo {
		height: 100%;
	}

	.bodyBorder {
		height: 88%;
	}

	.uni-margin-wrap {
		height: 100%;

	}

	.swiper {
		height: 100%;

	}

	.swiper-item {

		height: 100%;
		display: flex;
	}

	.swiper-border {
		display: flex;
		flex-direction: column;
		height: 100%;
		width: 98%;
	}

	.border-title {
		width: 100%;
		height: 60rpx;
		line-height: 60rpx;
		font-size: 24px;
		font-weight: 900;
		text-align: center;
	}

	.border-header {
		display: flex;
		flex-direction: row;
		width: 100%;
		height: 60rpx;
		line-height: 60rpx;
	}

	.td1 {
		width: 12%;
		text-align: center;
		margin: 0 auto;
		font-size: 14px;
		height: 120rpx;
		line-height: 120rpx;
	}

	.td2 {
		width: 12%;
		text-align: center;
		margin: 0 auto;
		font-size: 18px;
		font: bold;
		height: 60rpx;
	}

	.sroll-border {
		height: 90%;
		/* 		margin-top: 3%; */
	}

	.border-col {
		display: flex;
		flex-direction: row;
		height: 100%;
	}

	.tr2 {
		display: flex;
		flex-direction: row;
		width: 100%;
		height: 140rpx;
		line-height: 140rpx;
		text-align: center;
	}

	.main {
		margin: 30rpx;
		background-color: #FF6700;
		border-radius: 10rpx;
		border: 1px solid #FF6700;
	}

	.main .subject {
		height: 80rpx;
		font-size: 36rpx;
		text-align: center;
		line-height: 80rpx;
		color: #fff;
	}

	.main .body {
		padding: 20rpx;
		background-color: #FFFFFF;
	}

	.main .body .line {
		height: 60rpx;
		line-height: 60rpx;
	}

	.test {
		width: '200px';
		margin-left: 200px;
	}

	.body-border {
		width: 100%;
		height: 100%;

		display: flex;
		flex-direction: row;
	}

	.left-border {
		height: 100%;
		width: 30%;
	}

	.right-border {
		height: 100%;
		width: 65%;
		margin-left: 8%;
	}

	.chart1 {
		width: 100%;
		margin: 0 auto;
		margin-top: 5%;
		height: 60%;
		background-color: rgb(13, 38, 71, 0.5);
		/* opacity: 0.1; */
	}

	.echartsBorder {
		width: 300px;
		height: 250px;
	}

	.CountryGif {
		margin-top: 30px;
		width: 100%;
		height: 40%;

	}

	.gif_img {
		background: url(/static/2.gif);
		background-size: 100% 100%;
		background-repeat: no-repeat;
		padding-top: 56.25%;
	}

	.wrapper {
		padding: 0 30rpx;
		background-color: #F7F7F8;
		height: 100%;

		.orders-list {
			margin-right: 30rpx;
		}

		.number-total-title {
			display: flex;
			flex-direction: column;
			align-items: center;
			justify-content: center;
			border: 1rpx solid #fff;
			background-color: antiquewhite;
			border-radius: 20rpx;
			height: 200rpx;
			margin-top: 20rpx;

			.money-content {
				font-weight: bold;
				font-size: 36rpx;
				padding-top: 20rpx;
			}
		}

		.receive-money-number-hide {
			display: flex;
			align-items: center;
			justify-content: space-between;
		}

		.receive-money-number-show {
			display: flex;
			align-items: center;
			justify-content: center;
		}

		.receive-money-number {
			height: 160rpx;
			border: 1rpx solid #fff;
			background-color: #B0E2FF;
			border-radius: 20rpx;
			color: #CD5C5C;
			margin-top: 30rpx;
			padding: 0 20rpx;
			font-weight: bold;
			font-size: 30rpx;
		}

		.custom-style-btn {
			margin-top: 20rpx;
			width: 60%;
			height: 100rpx;
			background-color: #1E90FF;
			color: #fff;
		}

		.title-list {
			height: 50rpx;
			display: flex;
			align-items: center;
			justify-content: center;
		}

		.list-scall {
			height: calc(100vh - 670rpx);
			box-sizing: border-box;
			width: 100%;
		}

		.Border-header {
			width: 100%;
			font-size: 20px;
			font-weight: 800;
		}

		.header-list {
			width: 100%;
		}

		.base-text1 {
			text-align: center;

		}
	}
</style>