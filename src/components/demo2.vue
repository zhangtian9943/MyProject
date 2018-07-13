<template>
	<div>
		<h2>我是子</h2>
		<span>聊天记录：{{rows.history}}</span><br>
		<span>你收到的消息：{{rows.parentSayText}}</span><br>
		<span>你发送的消息：</span>
		<el-input
			type="textarea"
			:rows="3"
			placeholder="请输入内容"
			v-model="toldParent">
		</el-input>
		<el-button type="primary" @click="sendMessage">发送</el-button>
	</div>
</template>
<script>
export default {
	props: ['rows'],
	data () {
		return {
			toldParent: ''
		}
	},
	methods: {
		sendMessage() {
			this.$emit('child-told', this.toldParent)
			this.toldParent = ''
		}
	}
	
}
</script>

