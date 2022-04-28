<template>
	<div class="app">
		<h3>响应式数据的判断</h3>
	</div>
</template>

<script>
	import {reactive,toRefs,ref,readonly,isRef,isReactive,isReadonly,isProxy} from 'vue'
	export default {
		name: 'App',
		setup() {
			let car = reactive({name:'奔驰',price:'40W',})
			let sum = ref(0)
			let car2 = readonly(car)
			// 检查一个值是否为一个ref对象
			console.log(isRef(sum));
			// 检查一个对象是否是由reactive创建的响应式代理
			console.log(isReactive(car));
			// 检查一个对象是否是由readonly创建的只读代理
			console.log(isReadonly(car2));
			// 检查一个对象是否是由reactive或readOnly方法创建的代理
			console.log(isProxy(car));
			console.log(isProxy(car2));
			console.log(isProxy(sum));
	
			return {...toRefs(car)}
		}
	}
</script>

<style>
	.app{
		background-color: gray;
		padding: 10px;
	}
</style>

