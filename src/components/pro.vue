<template>
	<div>
		<h2>我是子</h2>
		<h3>捏出来的子信息：</h3>
		<ul>
			<li v-for="(item, index) in rows.infoBase"
			:key=index
			style="font-size: 15px; list-style-type: none">{{item.label}}{{item.value}}</li>
		</ul>
	</div>
</template>
<script>
export default {
	props: ['rows'],
	data () {    
		return {
			
			}
  },
  methods: {
    clickOn() {
    }
  }
  
}
</script>


