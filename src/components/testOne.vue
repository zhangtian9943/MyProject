<template>
	<div>
		<h2>测试1</h2>
		<el-button type="primary" @click="getDate">获取</el-button><br>
		<p>{{test}}</p>
	</div>
	
</template>
<script>
export default {
	data () {
		return {
			test: ''
		}
	},
	methods: {
		getDate() {
			this.test = window.localStorage.getItem(name)
		}
	}
}
</script>

