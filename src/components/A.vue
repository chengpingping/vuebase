<template lang="html">
	<div id="app">		
		组件A：{{msg}}
		<button @click="change" type="button" name="btn">change</button>
	</div>
</template>

<script>
	export default{
		data(){
			return{
				msg:"默认"
			}
		},
		methods:{
			change(){
				this.msg="改变"
			}
		}
	}
</script>

<style>
</style>