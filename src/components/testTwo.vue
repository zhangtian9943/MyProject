<template>
	<div>
		<h2>测试2</h2>
		<el-button type="primary" @click="getDate">获取</el-button><br>
		<p>游戏名称：{{gameName}}</p>
		<p>开发周期：{{gameDate}}</p>
		<p>开发引擎：{{gameEngine}}</p>
		<p>开发语言：{{gameLanguage}}</p>
		<p>打包平台：{{gamePlatForm}}</p>
	</div>
	
</template>
<script>
export default {
	data () {
		return {
			gameName: '',
			gameDate: '',
			gameEngine: '',
			gameLanguage: '',
			gamePlatForm: ''
		}
	},
	methods: {
		getDate() {
			this.gameName = window.localStorage.getItem('name')
			this.gameDate = window.localStorage.getItem('date')
			this.gameEngine = window.localStorage.getItem('engine')
			this.gameLanguage = window.localStorage.getItem('language')
			this.gamePlatForm = window.localStorage.getItem('platform')
		}
	}
}
</script>

