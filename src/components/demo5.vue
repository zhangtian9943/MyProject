<template>
  <div>
		<h2>总结：</h2>		
		<h3>第一次</h3>
		<span style="font-size: 15px">
			1.组件的特性： 使用方便，可复用，不同的参数传递于组件之间可产生不同的效果，达到开发的要求与目的。<br>
			2.父子间通信： 父组件向子组件通信：父组件可将对象或单一参数写入自定义元素（子组件）中，以属性的方式传递给子组件，<br>
			若此属性为 :date = "query",这里，date是传入子组件中的字段名，query是父组件赋值给date的字段名<br>（query必然是存在于父组件中的一个对象或是其它类型的值）
			子组件可以通过props['date']拿到父组件传递过来的值。在使用时，直接用this关键字取就可以了。若在dom中使用可直接写该字段的名字即可。<br>
			子组件向父组件通信：this.$emit('methods', value)方法。 第一个参数写父组件中监听接收的方法名，第二个参数写要传递的值，父组件监听此<br>方法要写在自组件的dom元素中，
			如：@childTold = "childMessage" ，childMessage是父组件要执行的函数名，此函数接收一个参数，这个参数就是子组件通信传递过来的value<br>
			值。
			3.兄弟组件之间通信： 通过this.$root.Bus.$emit方法与	this.$root.Bus.$on()方法实现，此处$emit和$on要写在一个公共的实例上才能触发。<br>
			在main.js中实例一个vue ,相当于是第三方。Bus: new Vue(). 在组件中使用$emit和$on方法便可实现通信了。这两个方法都有两个参数，<br>
			$emit第一个参数为要通信的组件接受的方法名，第二个参数为传递的值。$on第一个参数为接受的方法名，第二个参数为接收的值，注意，<br>
			$on方法要写到mounted生命周期函数中去。
			4.通过localStorage存储与获取达到通信的目的，window.localStorage.setItem(key, value)与window.localStorage.getItem(key)方法实现。<br> 
			set为存值，第一个参数是存入的名字，第二个参数为数据。get为取值，只有一个参数，该参数对应set的key值，通过这个key值拿到相对应存储的数据，进行赋值即可。<br>
			优点是操作简单，
			5.未达到要求： 通过vuex实现通信， 通过localStorage实现通信中遇到存储与取值出错的问题未解决.

		</span>
	</div>
</template>
<script>
export default {
	data () {
		return {
			
		}
	}
}
</script>

