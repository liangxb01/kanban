<template>
	<view class="item-page">
		<view class="base-scroll-list-rows-wrapper"
			:style="{height: `${pageHeight}px`}">
			<view
				class="base-scroll-list-rows"
				v-for="(item, index) in currentRowsData"
				:key="item.rowIndex"
				:style="{
					height: `${rowHeights[index]}px`,
					lineHeight: `${rowHeights[index]}px`,
				}"
				align="center"
			>
				<view class="base-scroll-list-columns base-scroll-list-text">
				<view style="display: flex;flex-direction: row;width: 100%;">
					<view class="base-text" style="width: 12%;">{{item.OrderNum}}</view>
					<view class="base-text"style="width: 7.5%;">{{item.Machine}}</view>
					<view class="base-text"style="width:7.5%">{{item.DueDate}}</view>
					<view class="base-text"style="width: 10%;">{{item.PlanPre}}</view>
					<view class="base-text"style="width: 30%">{{item.WorkDesc}}</view>
					<view class="base-text"style="width:10%;">{{item.Qty}}</view>
					<view class="base-text" style="width: 15%">{{item.OrderDate}}</view>
					<view class="base-text" style="width:7.5%;">{{item.CompletePre}}</view>
				</view>
				</view>
			</view>
		</view>	
	</view>
</template>
 
<script>
	import {deepClone} from '@/utils/deepCloneFu.js';
	export default {
		name: "ScrollList",
		props:{
			rowsDataProps: {
				type: Array,
				default () {
					return [];
				}
			}
		},
		data(){
			return {
				pageHeight: 800,
				isAnimationStart: true,
				currentRowsData: [],
				avgHeight: 0,
				rowHeights: [],
				rowNum: 10, // 展示的个数
				moveNum: 1, // 移动的位置 
				duration: 10000, // 动画间隔
				currentIndex: 0, // 动画指针
			}
		},
		watch: {
			// 该回调将会在侦听开始之后被立即调用
			rowsDataProps: {
				handler: function(val, oldVal) {
					this.updateChange()
				},
				deep: true
			},
		},
		mounted() {
			const query = uni.createSelectorQuery().in(this)
			// 页面高度
			query.select('.item-page').boundingClientRect((page) => {
				console.log('页面', page);
				this.pageHeight = page.height
				console.log('pageHeight', this.pageHeight);
			}).exec()	
		},
		methods: {
			updateChange() {
				this.stopAnimation();
				
				this.rowsData = this.rowsDataProps.map((item, index) => ({
				  rowIndex: index,
				  ...item
				}))
				
				// 如果rownum大于实际数据长度,则以实际数据长度为准
				if(this.rowNum > this.rowsData.length){
					this.rowNum = this.rowsData.length
				}
				this.avgHeight = (this.pageHeight / this.rowNum)-20;
				this.rowHeights = new Array(this.rowNum).fill(this.avgHeight)
				
				  // 展示动画
				this.isAnimationStart = true
				this.startAnimation()
			},
			// 开始动画
			async startAnimation() {
				if(!this.isAnimationStart) return;
				const totalLength = this.rowsData.length
				if(totalLength < this.rowNum) return;
				
				const index = this.currentIndex; 
				let _rowsData = deepClone(this.rowsData);
				// 将数据重新头尾链接
				const rows = _rowsData.slice(index)
				rows.push(..._rowsData.slice(0,index))
				this.currentRowsData = rows
				// 现将所有行的高度还原
				this.rowHeights = new Array(totalLength).fill(this.avgHeight)
				const waitTime = 300
				if(!this.isAnimationStart) return;
				await new Promise(resolve => setTimeout(resolve, waitTime));
				
				//将moveNum的行高度设置0
				this.rowHeights.splice(0, 1, 0)
				
				this.currentIndex += this.moveNum;
				// 是否到达最后一条数据
				const isLast = this.currentIndex - totalLength
				if(isLast >= 0) {
					//重置
					this.currentIndex = isLast
				}
				// sleep
				if(!this.isAnimationStart) return
				await new Promise(resolve => setTimeout(resolve, this.duration - waitTime))
				if(!this.isAnimationStart) return
				await this.startAnimation()
			},
			// 停止动画
			stopAnimation() {
				this.isAnimationStart = false
			},
		}
	}
</script>

<style lang="scss">
.item-page {
	height: 100%;
	width: 100%;
	.base-scroll-list-rows-wrapper {
		overflow: hidden;
		height: 100%;
		width: 100%;
	}
	.base-scroll-list-rows{
		display: flex;
		align-items: center;
		transition: all 0.3s linear;
	}
	.base-scroll-list-text {
	  // padding: 0rpx 10rpx;
	  // white-space: nowrap;
	  overflow: hidden;
	  // text-overflow: ellipsis;
	  // box-sizing: border-box;
	  flex: 1;
	}
	.base-scroll-list-columns {
	  height: 100%;
	}
	.base-text{
		align-items: center;
		// border:1px solid white;
		width: 100%;
	}
}
</style>

