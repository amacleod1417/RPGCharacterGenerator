<template>
    <div class="character-creator">
        <h1>Character Creator</h1>
        <label for="character-name">Character Name: </label>
        <input type="text" id="character-name" v-model="name" placeholder="Enter a name" /> <br /><br />
        <label for="professions-list">Character Profession: </label>
        <select id="professions-list" v-model="profession">
            <option value="Wizard">Wizard</option>
            <option value="Spy">Spy</option>
            <option value="Warrior">Warrior</option>
            <option value="Blacksmith">Blacksmith</option>
        </select>
        <p>{{name}}</p>
        <p>{{profession}}</p>
    </div>
</template>

<script>
    import axios from 'axios';

    export default {
        name: 'CharacterCreator',
        data: function () {
            return {
                name: null,
                profession: null
            }
        },
        methods: {
            postCharacter: function () {
                axios
                    .post('http://localhost:3000/characters', {
                        name: this.name,
                        profession: this.profession
                    });
            }
        }
    }
</script>

<style scoped>
</style>