<template>
    <div>
        <h3>Search: </h3>
        <input type="text" v-on:keyup="handleChange" v-model="searchValue">
    </div>
</template>

<script>
import { eventBus } from '../main.js'

export default {
    name: 'character-search',
    props: ['characters'],
    data(){
        return{
            searchValue: ""
        }
    },
    computed:{
        possibleCharacters: function () {
            return this.characters.filter((character) => {
              return character.name.toLowerCase().includes(this.searchValue.toLowerCase())
            })
        }
    },
    methods: {
        handleChange: function (){
            eventBus.$emit('search-changed', this.searchValue ? this.possibleCharacters:[])
        }
    }
}

</script>

<style>

</style>