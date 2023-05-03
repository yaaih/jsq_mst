<template>
	<view class="box">
		<view class="top">{{num}}</view>
		<view class="but">
			<view v-for="(item,index) in list" :key="index" :class="['btnall',item.classname]" @click="count(item.name)">{{item.name}}</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				num:'',
				sum:'',
				isjs:1,
				czf:'',
				list:[
					{classname:'czfclass',name:'AC'},
					{classname:'czfclass',name:'+/-'},
					{classname:'czfclass',name:'%'},
					{classname:'ysfclass',name:'÷'},
					{classname:'numclass',name:'7'},
					{classname:'numclass',name:'8'},
					{classname:'numclass',name:'9'},
					{classname:'ysfclass',name:'×'},
					{classname:'numclass',name:'4'},
					{classname:'numclass',name:'5'},
					{classname:'numclass',name:'6'},
					{classname:'ysfclass',name:'-'},
					{classname:'numclass',name:'1'},
					{classname:'numclass',name:'2'},
					{classname:'numclass',name:'3'},
					{classname:'ysfclass',name:'+'},
					{classname:'zeoclass',name:'0'},
					{classname:'numclass',name:'.'},
					{classname:'ysfclass',name:'='},
				]
			}
		},
		methods: {
			count(name){
				switch(name){
					case "AC":
						this.num = ''
						this.sum = ''
					break;
					case "+/-":
						this.num = this.num * -1
					break;
					case "%":
						this.num = parseFloat(this.num) / 100;
					break;
					case "÷":
						this.isjs = 0
						this.czf = '/'
					break;
					case "×":
						this.isjs = 0
						this.czf = '*'
					break;
					case "-":
						this.isjs = 0
						this.czf = '-'
					break;
					case "+":
						this.isjs = 0
						this.czf = '+'
					break;
					case ".":
						if(this.num.indexOf('.') == -1){
							this.num += '.'
							this.sum += '.'
						}
					break;
					case "=":
						this.num = eval(this.sum)
					break;
					default:
						if(!this.isjs){
							this.num = ''
							this.sum += this.czf
							this.isjs = 1
						}
						this.num += name
						this.sum += name
				}
			}
		}
	}
</script>

<style lang="less">
.box{
	width: 100%;
	height: 100%;
	display: flex;
	flex-direction: column;
	background: black;
	.top{
		width: 100%;
		height: 25%;
		box-sizing: border-box;
		padding: 30rpx;
		color: white;
		font-size: 80rpx;
		display: flex;
		align-items: flex-end;
		justify-content: flex-end;
	}
	.but{
		width: 100%;
		flex: 1;
		box-sizing: border-box;
		padding: 30rpx;
		display: flex;
		align-items: center;
		flex-wrap: wrap;
		justify-content: space-between;
		.btnall{
			width: 140rpx;
			height: 140rpx;
			line-height: 140rpx;
			text-align: center;
			border-radius: 50%;
			font-size: 50rpx;
		}
		.czfclass{
			background: #cccccc;
		}
		.numclass{
			background: #333333;
			color: white;
		}
		.ysfclass{
			background: orange;
			color: white;
		}
		.zeoclass{
			width: 320rpx;
			height: 140rpx;
			line-height: 140rpx;
			border-radius: 100rpx;
			text-align: left;
			box-sizing: border-box;
			padding-left: 52rpx;
			background: #333333;
			color: white;
		}
	}
}
</style>
