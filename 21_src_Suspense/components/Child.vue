<template>
	<div class="child">
		<h3>我是child组件</h3>{{sum}}
	</div>
</template>

<script>
	import {ref} from 'vue'
	export default {
		name: 'Child',
		// async  --异步
		// setup不能是一个async函数，因为返回值不再是return的对象, 
		// 而是promise, 模板看不到return对象中的属性。
		// 后期也可以返回一个Promise实例，但需要Suspense和异步组件的配合

	  async	setup() {
			let sum = ref(0)
			let p = new Promise((resolve,reject)=>{
				setTimeout(()=>{
					resolve({sum})
				},2000)
			})
			return await p
		}
	}
</script>

<style>
	.child{
		background-color: skyblue;
		padding: 10px;
	}
</style>