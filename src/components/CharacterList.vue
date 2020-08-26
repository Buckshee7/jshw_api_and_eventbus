<template>
    <ul>
        <li v-for="(character, index) in characters" :key="index">
            <character-select :character="character"></character-select>
        </li>
    </ul>
</template>

<script>
import CharacterSelect from './CharacterSelect.vue';

export default {
    name: 'character-list',
    props: ['characters'],
    components: {
        'character-select': CharacterSelect
    }
}
</script>

<style>

</style>