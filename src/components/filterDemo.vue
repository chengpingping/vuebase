<template>
	<div class="filterdemo">
		{{money|rmb}}
		{{40|rmb}}
		{{txt|author}}
	</div>
</template>

<script>
	export default{
		name:"filterdemo",
		data(){
			return{
				money:20,
				txt:"ok"
			}
		},
		filters:{
			rmb:function(value){
				if(!value){
					return ;
				}
				value=value.toString();
				return "￥"+value;
			},
			author:function(value){
				if(!value){
					return ;
				}
				value=value.toString();
				return "普希金——"+value;
			}
		}
	}
</script>

<style>
</style>