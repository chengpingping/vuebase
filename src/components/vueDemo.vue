<template>
	<div>
		<div class="old" :class="{active:classDemo,'txt':classDemo}">
		<!--{{msg.split('').reverse().join('')}}
		<div class="demo">
			{{getMsg}}
			{{mMsg()}}
		</div>-->
			css
		</div>
		<!--<div :class="{'a':c1,'c2':c2}">-->
		<div :class="cssObj">
			ci
		</div>
		<button @click="changeCss()" type="button">
				点击
		</button>
		<div :class="[isActive?activeClass:'' ,erroClass]">
			test1
		</div>
		<!--
        	对象中只能接受字符串，数组中可以接受对象
        -->
		<div class="old" :class="[isActive?active:'noactive',{'test':classDemo}]">
			应用中的样式
		</div>
		<div class="ipt">
			<input v-model.lazy="iptmsg" type="text" name="" value=""/>
			<input type="checkbox" v-model="checked" />
			<label for="checkbox">{{checked}}</label>
			<p>{{iptmsg}}</p>
		</div>
		{{myName}}
		<button @click="changeName()" type="button">改变名字</button>
	</div>
</template>

<script>
	export default {
		name:"vueDemo",
		data(){
			return{
				msg:"hello",
				classDemo:true,
				active:'act',
				c1:true,
				c2:false,
				cssObj:{
					'active':false,
					'c2':false
				},
				activeClass:'active',
				erroClass:'text-danger',
				isActive:true,
				helloC:'hc',
				iptmsg:"默认",
				checked:false,
				myName:"wqp"
			}
		},
		//计算属性
		computed:{
			getMsg(){
				return this.msg.split('').reverse().join('');
			}
		},
		methods:{
			mMsg(){
				return this.msg.split('').reverse().join('');
			},
			changeCss(){
				this.cssObj={
					"active":true,
					"c2":true
				}
			},
			changeName(){
				this.myName+="1";
			}
		},
		watch:{
			iptmsg(data){
				if(data==100)
					//console.log("");
					this.iptmsg="符合条件"
			},
			myName(data){
				console.log(data);
			}
		}
	}
</script lang="css">
<style>
.active{
	color: red;
}
.txt{
	font-size: 30px;
}
	
</style>