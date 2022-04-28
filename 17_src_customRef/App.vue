<template>
	<input type="text" v-model="KeyWord">
	<h3>{{KeyWord}}</h3>
</template>

<script>
	import {ref,customRef} from 'vue' 
	export default {
		name: 'App',
		setup() {
			// 自定义一个ref --名为: myref
			function myref(value,delay){
				let timer
				return customRef((track,trigger)=>{
					return {
						get(){
							console.log(`有人从myref这个容器中读取数据了,我把${value}给他了`);
							track()  //通知Vue追踪value的变化(提前和get商量一下，让它认为这个value是有用的)
							return value
						},
						set(newValue){
							console.log(`有人从myref这个容器中的数据改为了: ${newValue}`);
							clearTimeout(timer)
							timer = setTimeout(() => {
								value = newValue
								trigger()  //通知Vue去重新解析模板
							}, delay);
						}
					}
				})
			}
			// let KeyWord = ref('hello') //使用Vue提供的ref
			let KeyWord = myref('hello',500) 
			return {KeyWord}
		}
	}
</script>

