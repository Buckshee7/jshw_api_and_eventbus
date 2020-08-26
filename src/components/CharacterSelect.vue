<template>
  <p v-on:click="displayDetails"> {{ character.name }}</p>
</template>

<script>
import { eventBus } from '../main.js';

export default {
    name: 'character-select',
    props: ['character'],
    methods: {
        displayDetails: function() {
            eventBus.$emit('display-details', this.character)
        }
    }
}
</script>

<style>

</style>