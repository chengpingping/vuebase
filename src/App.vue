<template>
  <div id="app">
    <img src="./assets/logo.png">
    <HelloWorld/>
    <!--<VueDemo/>-->
    <!--引用-->
    <!--{{demo}}
    <input v-model="parentText" />
    <LearnVue @getMsg="getSonMsg" :title="parentText" />-->
    <!--<A />
    <B />-->
    <!--<component v-bind:is="currentComponent"></component>-->
    <!--<keep-alive>
    	<component v-bind:is="currentComponent"></component>
    </keep-alive>
    <button @click="changeComponent" type="button">切换组件</button>
    -->
    <!--<Parent/>-->
    <!--<Music/>-->
    <!--<SlotDemo/>-->
    <!--<SlotDemo>-->
    	<!--<template slot="v1">
    		<div class="v1">
    			插槽内容1
    		</div>
    	</template>
    	<template slot="v2">
    		<div class="v2">
    			插槽内容2
    		</div>
    	</template>-->
    	<!--<div class="">
    		hello插槽
    	</div>-->
    	<!--<template slot-scope="slotscope">
    		{{slotscope.ct}}
    	</template>-->
    <!--</SlotDemo>-->
    <!--<Anim/>-->
    <!--<FilterDemo/>-->
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'
import VueDemo from './components/vueDemo'
import LearnVue from './components/LearnVue'
import A from './components/A'
import B from './components/B'
import Parent from './components/parent'
import Music from './components/music'
import SlotDemo from './components/slotDemo'
import Anim from './components/anim'
import FilterDemo from './components/FilterDemo'
export default {
  name: 'App',
  data(){
  	return{
  		title:{
  			name:"jojo"
  			
  		},
  		demo:"",
  		parentText:"",
  		A:A,
  		B:B,
  		currentComponent:B
  	}
  },
  components: {
    HelloWorld,
    VueDemo,
    LearnVue,//注入
    A,
    B,
    Parent,
    Music,
    SlotDemo,
    Anim,
    FilterDemo
  },
  methods:{
  	getSonMsg(data){
  		this.demo=data
  	},
  	changeComponent(){
  		if(this.currentComponent=="A"){
  			this.currentComponent="B";
  		}else{
  			this.currentComponent="A";
  		}
  	}
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
