<template>
  <div class="hello">
    {{"hello".split('').reverse().join('')}}
    {{msg}}
    <p v-once>{{msg}}</p>
    <div v-html="hello"></div>
    <!--{{hello}}-->
    <a :href="url">{{url_name}}</a>
    <div :class="divClass">容器</div>
    <div :class="divClass2+'-1'">容器2</div>
    <div v-if="flag">孙悟空</div>
    <div v-else>通臂猿猴</div>
    <div v-show="flag">三国</div>
    <ul>
    	<li v-for="(item,index) in names" :key="index">{{index}}{{item.name}}</li>
    </ul>
    <ul>
    	<li v-for="(value,key,index) in obj" :key="index">{{value}}-{{key}}-{{index}}</li>
    </ul>
    <button @click="clickHandler('hahaha',$event)" type="button" name="btn">按钮</button>
    <ul>
    	<li v-for="item in helloArr">{{item}}</li>
    </ul>
    <button @click="addHandler()" type="button">添加</button>
  </div>
</template>

<script>export default {
	name: 'HelloWorld',
	data() {
		return {
			msg: 'Welcome to Your Vue.js App',
			hello: "<h3>hello H3</h3>",
			url_name: "百度",
			url: "http://www.baidu.com",
			divClass: 'isActive',
			divClass2: 'list',
			flag: false,
			names: [{
				name: "xiao",
				age: 29
			}, {
				name: "alice",
				age: 30
			}, {
				name: "jack",
				age: 23
			}],
			obj:{
				name:"ins",
				age:20
			},
			helloArr:["asa","dsas","dfvn"]
		}
	},
	mounted(){
		//get请求
		/*this.$axios.get("https://api.douban.com/v2/movie/top200")
		.then(res=>{
			console.log(res.data);
		})
		.catch(error=>{
			console.log(error);
		})*/
		var url=this.HOST+"/v2/movie/top200"
		this.$axios({
		  method: 'get',
		  url: url
		})
		.then(res=>{
			console.log(res.data);
		})
		.catch(error=>{
			console.log(error);
		})
	},
	methods:{
		clickHandler(data,$event){
			//改变数据
			this.flag=!this.flag;
			console.log(data);
			console.log(event);
		},
		addHandler(){
			//this.helloArr.push("hello");
			//this.helloArr.unshift("hello");
			console.log(this.helloArr.concat("hello","bye"));
		}
	}
}</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>h1,
h2 {
	font-weight: normal;
}


/*ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}*/

a {
	color: #42b983;
}</style>
