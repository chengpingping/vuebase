# vue简介
渐进式JavaScript框架（适合增删改查）
采用虚拟Dom
单页面视图层（包括路由）
ES5特性，支持IE8及以上
命令行工具CLI(脚手架)

# 1.安装vue
注意：node版本高于8.9
vue-cli3.x:npm install -g @vue/cli
vue-cli2.x:npm install -g @vue/cli-init

# 2.创建项目
vue init webpack my-project

注意：安装依赖，选择自己安装
安装项目：cnpm install
在项目的cmd下，运行npm start/npm run dev

# 3.工程项目

# 4.基础指令
mustache:{{变量}}只能存在单行语句
v-once:只能渲染一次
v-html:解析HTML结构
v-bind:指令（解析属性中的对象）
v-bind简写：（:）
v-if:条件渲染
v-else:
v-show:条件渲染

# 5.v-if和v-show
v-if:条件为真才渲染，更高的开销
v-show：不管条件是什么都会渲染；较好；如果运行时条件很少改变，则使用v-if较好

# 6.列表渲染
v-for：
:key :

# 7.事件的处理
	1.事件改变data数据，data数据改变引起视图变化
	2.事件传递参数
		$event
	3.数组检测更新
		push
		append
		unshift
		concat
		变异方法：
			改变原数组，则可以引起视图更新；
			不改变原数组，创建新数组，则无法引起视图更新；
# 8.计算属性
	独有属性
	计算属性和方法:
		1.函数每调用一次就计算一次；
		2.计算属性没有值改变就不会再计算

# 9.class和style绑定	

# 10.表单输入绑定
	修饰符：
		.lazy回车或者失去焦点以后才能响应
		.number只接受数字类型
		.trim去掉前后空格
	watch：实时监听数据变化，进行过滤操作
		计算属性和监听属性：
			
# 11.组件的创建
	在App.vue中：
		1.import 文件
		2.注入组件
		3.引用组件
		
# 12.组件的基础
	组价的作用：增强复用性
	data必须是一个函数
	## 1.组件传递数据（通过props）
		父传子；
	## 2.单个根元素
	
	## 3.自定义事件向父级组件发送消息
	    $emit()
		子传父；必须通过事件发送
		v-modle也可以实现；
	
# 13.动态组件
	component：
	keep-alive:避免重复渲染，保存切换状态
	
# 14.Prop特性
	用于父组件向子组件传递数据；
	数组和对象传递数据要用方法；

# 15.处理边界情况
	this.$root.foo：
		在main.js中可以声明全局变量；可以读取也可以修改：
		代替父组件利用prop传递数据的方法
		低耦合，高内聚
	操作原生dom:
		使用属性ref和mounted方法：this.$refs.p1
		
# 16.插槽
	<slot></slot>
	作用：传递视图，内容分发
	效果：内容展示由父组件传递给子组件（UI是由父组件传递的），UI上的内容由子组件决定
	具名插槽：使用name属性和标签<template slot="name">
	插槽默认数据：
	编译作用域：父组件中定义的插槽就在父组件中定义数据；反之，在子组件中定义。
	作用域插槽：希望有一个由子组件提供数据的复用插槽

# 17.vue的生命周期

				new vue()
			init event&lifecycle
	1.创建之前
		beforeCreate
			init injection&reactivty
	2.创建之后
		created
				has "el" option
	3.渲染之前
		beforeMount
	4.渲染之后
		mounted
	5.更新之前
		beforeUpdate
	6.更新之后
		updated
	7.销毁之前
		beforeDestroy
	8.销毁之后
		destroyed
	
# 18.动画效果
	指令：v-if和v-show
	组件：transition
	过渡：transition，opacity
	动画：@keyframs规则，或者第三方 CSS 动画库 Animate.css
		
# 19.自定义指令
	input获得焦点：
		directive
		钩子函数：bind只调用一次；inserted：被绑定元素插入父节点时调用；update：更新时调用；unbind:只调用一次，指令与元素解绑时调用。
		钩子函数的参数：el:指定操作元素
		binding：一个对象包含以下属性：
			name:指令名，不包括v-前缀；
			value：指令绑定值；
		vnode:vue编译生成的虚拟节点
		oldVnode:上一个虚拟节点
	全局指令
		在main.js中定义；
	局部指令
		在组件中定义

# 20.过滤器
	filters:
	使用：数据|过滤函数
# 21.网络请求axios:
	react中使用fetch
	在这之前，vue官方维护了一个网络请求：vue-resource；后期不维护了
	## 推荐使用axios(插件):
		基于promise
	## 安装：
		使用npm:npm install axios --save
	## 引入：
		在main.js中引入：
		import Axios from 'axios'
		Vue.prototype.$axios=Axios
	## 使用
	//get请求
		mounted(){
			
			this.$axios.get("https://www.baidu.com")
			.then(res=>{
				console.log(res.data);
			})
			.catch(error=>{
				console.log(error);
			})
		}
		get两种参数请求：
		1.在链接后直接加上：?参数名=参数值...
		2.在链接的引号后,qs.stringfy({
			参数名:"参数值",
			...
		})
	//post请求
	import qs from "qs"//解决格式转码问题 ?参数名=参数值...
	mounted(){
			
			this.$axios.post("https://www.baidu.com",{
				params:{
					参数名:"参数值",
					...
				}
			})
			.then(res=>{
				console.log(res.data);
			})
			.catch(error=>{
				console.log(error);
			})
		}
		//标准写法
		axios({
		  method: 'post',
		  url: '/user/12345',
		  data: {
		    firstName: 'Fred',
		    lastName: 'Flintstone'
		  }
		});
## 22.axio全局配置
	axios.defaults.baseURL = 'https://api.example.com';
	axios.defaults.headers.common['Authorization'] = AUTH_TOKEN;
	axios.defaults.headers.post['Content-Type'] = 'application/x-www-form-urlencoded';
	
## 23.拦截器
	import qs from "qs"
	// 添加请求拦截器（发送数据之前）
	axios.interceptors.request.use(function (config) {
	    // 在发送请求之前做些什么
	    if(config.method==="post"){
	    	config.data = qs.stringify(config.data)
	    }//不用在post传参的时候转换类型
	    return config;
	  }, function (error) {
	    // 对请求错误做些什么
	    return Promise.reject(error);
	  });
	
	// 添加响应拦截器（接收数据之前）
	axios.interceptors.response.use(function (response) {
	    // 对响应数据做点什么
	    if(response.data){
	    	return{
	    		msg："数据返回不合理";
	    	} 
	    }
	    return response;
	  }, function (error) {
	    // 对响应错误做点什么
	    return Promise.reject(error);
	  });
	 
## 24.处理跨域问题
在config/index.js文件中配置
	proxyTable: {
    	'/douban_api':{
    		target:'https://api.douban.com',
    		pathRewrite:{
    			'^/douban_api':''
    		},
    		changeOrigin:true
    	}
    },
在main.js中配置
	Vue.prototype.HOST="/douban_api"
重启服务器

重新设置网络请求(访问)
	var url=this.HOST+"/v2/movie/top200"
	this.$axios({
	  method: 'post',
	  url: url
	})


