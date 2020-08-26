<template>
    <div>
        <div>
            <img :src="character.image" :alt="`${character.name}'s image`">
        </div>
        <div>
            <h3>{{ character.name }}</h3>
            <p>Species: {{ character.species }}</p>
            <p>Status: {{ character.status }}</p>
        </div>
    </div>
</template>

<script>
import { eventBus } from '../main.js';

export default {
    name: 'character-detail',
    props: ['character']
}
</script>

<style>

</style>