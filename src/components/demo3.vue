<template>
	<div>
		<h2>demo3</h2>
		<span>店名：</span>
		<el-select v-model="query.shopName" placeholder="店名" :disabled="canView">
			<el-option
				v-for="item in shopType"
				:key="item.value"
				:label="item.label"
				:value="item.value">
			</el-option>
		</el-select>
		<span>注册资金：</span>
		<el-select v-model="query.money" placeholder="请选择" :disabled="canView">
			<el-option
				v-for="item in moneyType"
				:key="item.value"
				:label="item.label"
				:value="item.value">
			</el-option>
		</el-select>
		<span>开店日期：</span>
		<el-date-picker
      v-model="query.shopDay"
      type="date"
      placeholder="选择日期"
			:disabled="canView">
    </el-date-picker><br>
		<span>地址：</span>
		<el-input v-model="query.address" placeholder="请输入地址" style="width: 226px" :disabled="canView"></el-input>
		<span>法人代表：</span>
		<el-input v-model="query.bossName" placeholder="法人代表" style="width: 226px" :disabled="canView"></el-input><br>
		<el-button type="primary" @click="approval" :disabled="canView">审批</el-button>
	</div>
</template>
<script>
export default {
	data () {
		return {
			shopType: [{
          value: '1',
          label: '非法走私'
        }, {
          value: '2',
          label: '芝麻开花'
        }, {
          value: '3',
          label: '热情海洋'
        }, {
          value: '4',
          label: '零零散散'
        }, {
          value: '5',
          label: '北京烤鸭'
        }],
				moneyType: [{
          value: '1',
          label: '50W以下'
        }, {
          value: '2',
          label: '50-100W'
        }, {
          value: '3',
          label: '101-500W'
        }, {
          value: '4',
          label: '500-100W'
        }, {
          value: '5',
          label: '1000W以上'
				}],
				query: {
					shopName: '',
					money: '',
					shopDay: '',
					address: '',
					bossName: '',
				},
				canView: false
		}
	},
	mounted () {
		this.$root.Bus.$on('brotherTold', val => {
			if (val === true) {
				this.canView = false
				alert('恭喜，审核通过')
			} else {
				this.canView = false
				alert('审核失败，请检查您填写的内容')
			}
		})
	},
	methods: {
		approval() {
			this.$root.Bus.$emit('demoTold', this.query)
			this.canView = true			
		}
	}
}
</script>

