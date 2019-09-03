<template lang="html">
	<div class="music">
		音乐实例
		<p class="" ref="p1">元素</p>
		<audio ></audio>
	</div>
</template>

<script>
	export default{
		name:"music",
		data(){
			return{
				
			}
		},
		mounted(){
			console.log(this.$refs.p1);
			this.$refs.p1.innerHTML="改变"
		}
	}
</script>

<style>
</style>