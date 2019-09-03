<template lang="html">
	<!--只有一个根容器-->
	<div id="app" class="continer">
		新的组件{{title}}
		<input v-model="searchText" />
		<button @click="sendMsg" type="button" name="btn">传递数据</button>
	</div>
</template>

<script>
	export default{
		name:'learn',//当前组件名称
		data(){//所有的初始化状态放在这里
			return{
				searchText:""
			}
		},
		props:["title"],
		methods:{
			sendMsg(){
				this.$emit("getMsg",this.searchText)
			}
		}
	}
</script>

<!--样式-->
<!-- Add "scoped"(作用域 )attribute to limit CSS to this component only -->
<style lang="css" scoped>
	.continer{
		background: red;
	}
</style>