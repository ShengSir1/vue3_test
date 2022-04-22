<template>
	<Demo @hello="showHelloMsg" msg="你好啊" school="尚硅谷">
		<template v-slot:qwe> //Vue3中推荐使用 v-slot:??? Api, 不推荐slot="" API写法(版本兼容性问题) 
			<span>尚硅谷</span>
		</template>
		<template v-slot:asd>
			<span>尚硅谷</span>
		</template>
	</Demo>
</template>

<script>
	import Demo from './components/Demo'
	export default {
		name: 'App',
		components:{Demo},
		setup(){
			function showHelloMsg(value){
				alert(`你好啊，你触发了hello事件，我收到的参数是:${value}！`)
			}
			return {
				showHelloMsg
			}
		}
	}
</script>

