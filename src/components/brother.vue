<template>
    <div>
			<h2> brother</h2>
			<div v-show="canshow">
				<h3>核对审批信息</h3>
				<span>店名：</span>
				<el-select v-model="demoDate.shopName" placeholder="店名" disabled>
					<el-option
						v-for="item in shopType"
						:key="item.value"
						:label="item.label"
						:value="item.value">
					</el-option>
				</el-select>
				<span>注册资金：</span>
				<el-select v-model="demoDate.money" placeholder="请选择" disabled>
					<el-option
						v-for="item in moneyType"
						:key="item.value"
						:label="item.label"
						:value="item.value">
					</el-option>
				</el-select>
				<span>开店日期：</span>
				<el-date-picker
					v-model="demoDate.shopDay"
					type="date"
					placeholder="选择日期"
					disabled>
				</el-date-picker><br>
				<span>地址：</span>
				<el-input v-model="demoDate.address" placeholder="请输入地址" style="width: 226px" readonly></el-input>
				<span>法人代表：</span>
				<el-input v-model="demoDate.bossName" placeholder="法人代表" style="width: 226px" readonly></el-input><br>
				<el-button type="primary" @click="passClick">通过</el-button>
				<el-button type="primary" @click="failedClick">驳回</el-button>
			</div>
		</div>
</template>
<script>
export default {
	data () {
		return {
			demoDate: {
				shopName: '',
				money: '',
				shopDay: '',
				address: '',
				bossName: '',
			},
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
			canshow: false
		}
	},
	mounted () {
		this.$root.Bus.$on('demoTold', val => {
			this.demoDate = val
			this.canshow = true
		})
	},
	methods: {
		passClick() {
			this.canshow = false
			this.$root.Bus.$emit('brotherTold', true)
			this.restDate()
		},
		failedClick() {
			this.canshow = false
			this.$root.Bus.$emit('brotherTold', false)
			this.restDate()
		},
		restDate() {
			for(const key in this.demoDate) {
				this.demoDate[key] = ''				
			}
		}
	}
}
</script>

