<template>

  <div class="container">
  <ul>
    <li v-for="trivia in trivias" :key="trivia.id" @click="toggleTrivia(trivia.id)">
    {{ trivia.question }}

    </li>
  </ul>
   
  </div>
</template>

<script>
import { mapGetters, mapActions } from 'vuex';
export default {
  name: 'TriviaApp',
  data(){
    return {
      selectedTriviasIDs:[]
    }
  },
  computed: {
    ...mapGetters({
      trivias: "getTrivias"
    })
  },
  methods: {
    ...mapActions([
      'fetchTrivias'
      ]
    ),

    toggleTrivia(triviaId){
      let triviaIdIndex = this.selectedTriviasIDs.indexOf(triviaId)
      let isSelectedTriviaId = triviaIdIndex >-1;
      if(isSelectedTriviaId) {
        return this.selectedTriviasIDs.splice(triviaIdIndex, 1)
      }
      this.selectedTriviasIDs.push(triviaId);
    }
  },
  created(){
    this.fetchTrivias();
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

