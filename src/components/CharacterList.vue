<template>
    <div>
        <h3>Matches:</h3>
        <ul>
            <select v-on:change="displayDetails" v-model="selectedCharacterFromList">
                <option v-if="!selectedCharacter" disabled>Choose a character</option>
                <option v-for="(character, index) in characters" :key="index" :value="character">{{ character.name }}</option>
            </select>
        </ul>
    </div>
</template>

<script>
import CharacterSelect from './CharacterSelect.vue';
import { eventBus } from '../main.js';

export default {
    name: 'character-list',
    data(){
        return{
            selectedCharacterFromList: null
        }
    },
    props: ['characters', 'selectedCharacter'],
    components: {
        'character-select': CharacterSelect
    },
    methods: {
        displayDetails: function() {
            eventBus.$emit('display-details', this.selectedCharacterFromList)
        }
    }
}
</script>

<style>

</style>