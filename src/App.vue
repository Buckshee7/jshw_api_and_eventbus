<template>
  <div>
    <h1>Rick and Morty Characters</h1>
    <div class="flex">
      <character-search :characters="characters"></character-search>
      <character-list :characters="possibleCharacters.length > 0 ? possibleCharacters:characters" :selectedCharacter="selectedCharacter"></character-list>
      <character-details v-if="selectedCharacter" :character="selectedCharacter"></character-details>
    </div>
  </div>
</template>

<script>
// Import components
import CharacterList from './components/CharacterList.vue';
import CharacterDetails from './components/CharacterDetail.vue';
import CharacterSearch from './components/CharacterSearch.vue';
import { eventBus } from './main.js';

export default {
  name: 'app',
  data(){
    return{
      characters: [],
      selectedCharacter: null,
      possibleCharacters: []
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
  
    eventBus.$on('display-details', (character) => {this.selectedCharacter = character ? character:null});
    eventBus.$on('search-changed', (list) => {
      this.possibleCharacters = list
      eventBus.$emit('display-details', list[0] ? list[0]:"")
      });
  },
  components: {
    'character-list': CharacterList,
    'character-details': CharacterDetails,
    'character-search': CharacterSearch
  }
}
</script>

<style>
.flex{
  display: flex;
}
</style>