<template>
  <div>
    <h1>Rick and Morty Characters</h1>
    <div class="flex">
      <character-list :characters="characters"></character-list>
      <character-details :character="selectedCharacter"></character-details>
    </div>
  </div>
</template>

<script>
// Import components
import CharacterList from './components/CharacterList.vue';
import CharacterDetails from './components/CharacterDetail.vue';
import { eventBus } from './main.js';

export default {
  name: 'app',
  data(){
    return{
      characters: [],
      selectedCharacter: null
    }
  },
  methods: {
    apiCall: function(){
        // Grab API data
        fetch('https://rickandmortyapi.com/api/character/')
        .then((request) => request.json())
        .then((data) => this.characters = data.results);
    }
  },
  mounted() {
    this.apiCall();

    eventBus.$on('display-details', (character) => {this.selectedCharacter = character});
  },
  components: {
    'character-list': CharacterList,
    'character-details': CharacterDetails
  }
}
</script>

<style>
.flex{
  display: flex;
}
</style>