<template lang="html">
	<div id="child">
		子组件:{{title}}/{{age}}<br />
		<p>称号：{{nick}}</p>
		<p>父亲：{{parent}}</p>
		<p>女朋友们：{{girlfriends}}</p>
		<ul>
			<li v-for="girl in girlfriends">{{girl}}</li>
		</ul>
		{{getFoo}}
		<button @click="sendMoney" type="button" name="btn">反馈</button>
	</div>
</template>

<script>
	export default{
		name:"child",
		data(){
			return{
				msg:"child"
			}
		},
//		props:["title","age"],
		props:{
			title:String,
			age:Number,
//			nick:String
			nick:{
				type:String,
				default:"国名老公"
			},
			parent:{
				type:String,
				required:true//必选项
			},
			//默认值如果是数组，或者对象，必须返回一个function
			girlfriends:{
				type:Array,
				default:function(){
					return ["g1","g2"]
				}
			}
		},
		methods:{
			sendMoney(){
				this.$emit("money","翻了5倍");
			}
		},
		computed:{
			getFoo(){
				return this.$root.foo;
			}
		}
	}
</script>

<style lang="css">
</style>