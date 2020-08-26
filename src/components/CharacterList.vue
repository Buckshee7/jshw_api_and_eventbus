<template>
    <ul>
        <select v-on:change="displayDetails" v-model="selectedCharacter">
            <option disabled>Choose a character</option>
            <option v-for="(character, index) in characters" :key="index" :value="character">{{ character.name }}</option>
        </select>
    </ul>
</template>

<script>
import CharacterSelect from './CharacterSelect.vue';
import { eventBus } from '../main.js';

export default {
    name: 'character-list',
    data(){
        return{
            selectedCharacter: null
        }
    },
    props: ['characters'],
    components: {
        'character-select': CharacterSelect
    },
    methods: {
        displayDetails: function() {
            eventBus.$emit('display-details', this.selectedCharacter)
        }
    }
}
</script>

<style>

</style>