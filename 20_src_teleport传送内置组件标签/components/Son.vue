<template>
	<div class="son">
		<h3>我是Son组件</h3>
		<Dialog/>
	</div>
</template>

<script>
	import Dialog from './Dialog'
	export default {
		name: 'Son',
		components:{Dialog}
	}
</script>

<style>
	.son{
		background-color: yellow;
		padding: 10px;
	}
</style>