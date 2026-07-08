<script>
import CharacterFacts from './components/CharacterFacts.vue'
export default {
  components: {
    CharacterFacts,
  },
  data: () => ({
    newCharacter: {
      name: '',
      drink: [],
    },
    characterList: [
      {
        name: 'The Dude',
        drink: ['cosmo', 'white russian'],
      },
      {
        name: 'Maude',
        drink: ['cosmo', 'wine'],
      },
      {
        name: 'Walter',
        drink: ['soda', 'coffee', 'root beer'],
      },
      {
        name: 'Donny',
        drink: ['root beer', 'Mt. Dew'],
      },
    ],
    favoriteCharacter: [],
  }),

  methods: {
    addNewCharacter() {
      this.characterList.push(this.newCharacter)
      this.newCharacter = { name: '', drink: '' }
    },
    makeFavorite(character) {
      this.favoriteCharacter.push(character)
    },
  },
}
</script>
<CharacterFacts :characters="characterList" />
<template>
  <ul v-if="favoriteCharacter.length > 0">
    <li v-for="(actor, index) in favoriteCharacter" :key="`actor-${index}`">
      {{ actor.name }}
    </li>
  </ul>
  <p v-else>There are no favorite Characters</p>
</template>
