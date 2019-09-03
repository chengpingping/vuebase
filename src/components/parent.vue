<template lang="html">
	<div id="parent">
		父组件:{{money}}
		<Child @money="getMoney" :girlfriends="girlfriends" parent="王健林" nick="娱乐圈" :age="age" title="有一个小目标"/>
		<!--<SlotDemo/>-->
		<SlotDemo>
			<div slot-scope="slotProps">
				<h1>{{slotProps.ct}}</h1>
			</div>
		</SlotDemo>
	</div>
</template>

<script>
import Child from './child'
import SlotDemo from './slotDemo'
	export default{
		name:"parent",
		data(){
			return{
				msg:"parent",
				money:"赚了吗？",
				age:20,
				girlfriends:["张予曦","豆豆","其他"]
			}
		},
		components:{
			Child,
			SlotDemo
		},
		methods:{
			getMoney(data){
				this.money=data;
			}
		}
	}
</script>

<style lang="css">
	
</style>