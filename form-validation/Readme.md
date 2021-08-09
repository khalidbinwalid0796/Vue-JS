parent component-->
<component :is='componentName' @change="componentChange"></component>
	aikhane parameter pass na korar sotte o niche methods ar vitore 
	componentChange(newComp) parameter pass kora hoyese

child component-->
<template id="signUpForm">
	<small><a class="pull-right" @click='changeToTnc' href="#">Terms and Conditions</a></small>
</template>

<template id="tnc">
	<button class="btn btn-success" @click='back_to_signup'>Back To Login</button>
</template>

emit example-->parent a hello world ase oita click korle child ar bangladesh dekhabe.

Vue.component('signUpForm',{
	template:'#signUpForm',

	methods:{
		changeToTnc(){
			this.$emit('change','tnc'); 
			//ai change name parent component event hobe
			//2nd parameter holo data jeta changeToTnc() ar parameter hisabe pass hoy but aikhane hoy ne; tnc holo component name
		}
	}
});


Vue.component('tnc',{
	template:'#tnc',

	methods:{
		back_to_signup(){
			this.$emit('change','signUpForm'); //ai change name parent component event hobe
			//2nd parameter holo data jeta back_to_signup() ar parameter hisabe pass hoy but aikhane hoy ne;; signUpForm holo component name
		}
	}
});

parent component-->

new Vue({
	el:'#app',
	data:{
		componentName:'signUpForm'
	},
	methods:{
		componentChange(newComp){
			this.componentName = newComp;
		}
	}
})