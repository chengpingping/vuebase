<template>
	<div class="anim">
		<button v-on:click="showHide" type="button">Toggle</button>
		<!--<transition name="fade">
			<p class="box" v-if="show">hello</p>
		</transition>-->
		<transition
			name="custom-classes-transition"
			enter-active-class="animated zoomInUp"
			leave-active-class="animated zoomOutDown"
			
		>
			<p class="box" v-if="show">hello</p>
		</transition>
		<input v-focus type="text" />
		<p v-mystyle >hahah</p>
	</div>
</template>

<script>
	export default{
		name:"anim",
		data(){
			return{
				show:true
			}
		},
		methods:{
			showHide(){
				this.show=!this.show;
			}
		},
		directives:{
			focus:{
				inserted:function(el){
					el.focus();
				}
			},
			mystyle:{
				inserted:function(el){
					el.style.fontSize="40px";
					//el.cssText="   "
				}
			}
		}
	}
</script>

<style>
	/*.fade-enter-active,.fade-leave-active{
		transition: opacity .5s;
	}
	.fade-enter,.fade-leave-to{
		opacity: 0;
	}*/
	/*
	 两种状态enter,leave
	 
	 */
	/*.fade-enter,.fade-leave-to{
		opacity:0;
	}
	.fade-enter-to,.fade-leave{
		opacity:1;
	}
	.fade-enter-active,.fade-leave-active{
		transition: opacity .5s;
	}*/
	.box{
		height: 100px;
		width:100px;
		background-color:red;
	}
	/*.fade-enter,.fade-leave-to{
		opacity:0;
		width: 0;
		height: 0;
	}
	.fade-enter-to,.fade-leave{
		opacity:1;
		width: 100px;
		height: 100px;
	}
	.fade-enter-active,.fade-leave-active{
		transition: all 5s;
	}*/
	/*.fade-enter,.fade-leave-to{*/
		/*animation: bounce-out .5s;*/
		/*animation: bounce-in .5s reverse;
	}
	.fade-enter-to,.fade-leave{
		animation: bounce-in .5s;
	}
	.fade-enter-active,.fade-leave-active{
		
	}
	@keyframes bounce-in{
		0%{
			transform: scale(0);
		}
		50%{
			transform: scale(1.5);
		}
		100%{
			transform: scale(1);
		}
	}
	@keyframes bounce-out{
		0%{
			transform: scale(1);
		}
		50%{
			transform: scale(1.5);
		}
		100%{
			transform: scale(0);
		}
	}*/
</style>