<template>
	<table>
		<tr>
			<th>输出</th>
			<th>刘老师</th>
			<th>少良兄</th>
			<th>皮皮欢</th>
			<th>varcyan</th>
		</tr>
		<!-- <el-input v-model="input" placeholder="请输入内容" @change="a"></el-input> -->
		<tr v-for="(item,index) in list">
			<td>
				<!-- <el-input v-model="item.export" placeholder="请输入内容" @change="calc(item)"></el-input> -->
				<input v-model="item.export" v-on:input="calc(item)">
			</td>
			<td>
				<el-checkbox v-model="item.liu">备选项</el-checkbox>
			</td>
			<td>
				<el-checkbox v-model="item.ma">备选项</el-checkbox>
			</td>
			<td>
				<el-checkbox v-model="item.huan">备选项</el-checkbox>
			</td>
			<td>
				<el-checkbox v-model="item.xu">备选项</el-checkbox>
			</td>
		</tr>
		<tr>
			<td>合计：</td>
			<td>{{allList.liu}}</td>
			<td>{{allList.ma}}</td>
			<td>{{allList.huan}}</td>
			<td>{{allList.xu}}</td>
		</tr>
	</table>
</template>
<script>
  export default {
	data() {
		return {
			input: '',
			list: [
				{
					export: '',
					liu: false,
					ma: false,
					huan: false,
					xu: false,
					itemAll: 0
				}
			],
			allList: {
				liu: 0,
				ma: 0,
				huan: 0,
				xu: 0
			},
			aver: 0
		}
	},
	methods: {
		a () {
			console.log('change')
		},

		calc (item) {
			this.aver = 0;
			let _arr = [];	// 用于存放已选择的数据
			
			Object.keys(this.allList).map(one => {
				if (item[one]) _arr.push(one);
			})
			console.log(_arr);
			this.aver = item.export / _arr.length;
			// console.log(this.aver);
			_arr.map(one => {
				// console.log(this.allList[one])
				// this.allList[one] += this.aver;
				this.allList[one] = this.allList[one] + this.aver
			})
		}
	}
  };
</script>
<style>
	table, th, td {
		border: 1px solid #ddd;
		border-collapse:collapse;
	}
	th {
		padding: 6px;
	}
	td {
		padding: 6px 10px;
	}
</style>