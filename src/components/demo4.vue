<template>
	<div>
		<span>游戏名称：</span>
		<el-input v-model="query.name" placeholder="游戏名称" style="width: 226px"></el-input>
		<span>开发周期:</span>
		<el-input v-model="query.date" placeholder="开发周期" style="width: 226px"></el-input>
		<span>开发引擎:</span>
		<el-input v-model="query.engine" placeholder="开发引擎" style="width: 226px"></el-input>
		<span>开发语言:</span>
		<el-input v-model="query.language" placeholder="开发语言" style="width: 226px"></el-input>
		<span>打包平台:</span>
		<el-input v-model="query.platform" placeholder="打包平台" style="width: 226px"></el-input><br>
		<el-button type="primary" @click="transfeClick">传输</el-button>
	</div>
</template>
<script>
export default {
	data () {
		return {
			query: {
				name: '',
				date: '',
				engine: '',
				language: '',
				platform: ''
			}
		}
	},
	methods: {
		transfeClick() {
			// 此处获取有问题 可能情况使 存储只能存一个值，这个可能性比较小 未解决
			window.localStorage.setItem(name, this.query.name)
			window.localStorage.setItem(date, this.query.date)
			window.localStorage.setItem(engine, this.query.engine)
			window.localStorage.setItem(language, this.query.language)
			window.localStorage.setItem(platform, this.query.platform)


			var sgds = window.localStorage.getItem(date)
			console.log(date)
		}
	}
}
</script>

