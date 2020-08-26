<template>
    <div>
        <p>{{ character.name }}</p>
        <p>{{ character.species }}</p>
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