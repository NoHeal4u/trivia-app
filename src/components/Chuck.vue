<template>
	<div class="container">

	
  <!--  Dje si Chuck! {{ randomJoke.value }}  -->
   <div class="card" style="width: 18rem;">
  <img class="card-img-top" 
    :src="randomJoke.iconUrl" 
    alt="Card image cap">
  <div class="card-body">
     <p class="card-text"
     v-text="randomJoke.value">
     </p>
     <input class="form-control mb-2"
      type="text"
       placeholder= "Enter joke category..."
        @input="setCategory"
        >
     <a @click="getNewJoke" class="btn btn-primary">Get new joke</a>
  </div>
</div>
    </div>
</template>
		


	

<script>

import { mapGetters, mapActions, mapMutations } from 'vuex'; //map actions vise nije potreban jer smo import store
import { store } from './../store';

//[1,2,3]=> ...[1,2,3] => 1,2,3
//const c = [x,y] => mapCoordinates(c[0], c[1]) =>mapCoordinates(...c)
	export default {
		name: 'Chuck',

		computed:{
			...mapGetters({
				randomJoke: 'getRandomJoke'  
			})
		},

		methods: {

			...mapMutations([

				'setJokeCategory'

			]),

			getNewJoke(){
				store.dispatch('fetchRandomJoke', ()=>{} ); //anonimna da bi mogla next bez pucanja
			},

			setCategory(event){
				this.setJokeCategory(event.target.value);

			},
		},

		// methods: {
		// 	...mapActions([
		// 		'fetchRandomJoke'])
		// }, ne treba vise jer smo isli preko stora

		// created(){
		// 	this.fetchRandomJoke();
		// },

		beforeRouteEnter(to, from, next){
			store.dispatch('fetchRandomJoke', next );
			// next();

		}

	}

</script>