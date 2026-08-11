<script>
import DrinkStatistics from './components/DrinkStatistics.vue'
import CharacterCard from './components/CharacterCard.vue'
export default {
  components: {
    DrinkStatistics,
    CharacterCard,
  },
  data: () => ({
    newCharacter: {
      name: '',
      drink: [],
    },
    characterList: [
      {
        name: 'The Dude',
        drink: ['Cosmo', 'White Russian'],
      },
      {
        name: 'Maude',
        drink: ['Cosmo', 'wine'],
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
    favoriteList: [],
    Movies: [
      {
        title: 'Big Lebowski',
        cast: [
          { name: 'Jeff Bridges', characterName: 'The Dude', favorite: false },
          { name: 'Smita Pallod', characterName: 'Maude', favorite: false },
        ],
      },
      {
        title: 'Star Wars',
        cast: [
          { name: 'Mark Hamill', characterName: 'Luke Skywalker', favorite: false },
          { name: 'Carrie Fisher', characterName: 'Leia', favorite: false },
        ],
      },
    ],
  }),
  methods: {
    addNewCharacter() {
      this.characterList.push(this.newCharacter)
      this.newCharacter = { name: '', drink: '' }
    },
    addFavoriteCharacter(payload) {
      this.favoriteList.push(payload)
    },
  },
}
</script>
<template>
  <DrinkStatistics :characters="characterList" />
  <h2>The Big Lebowski</h2>
  <h2>Characters</h2>
  <ul v-if="characterList.length > 0">
    <li v-for="(character, index) in characterList" :key="`even-character-${index}`">
      <CharacterCard :character="character" @favorite="addFavoriteCharacter" />
    </li>
  </ul>
  <p v-else>There are no characters</p>
  <p>Enter your favorite character</p>
  <pre>
        {{ newCharacter }}
    </pre
  >
  <input
    type="text"
    placeholder="Enter Character"
    v-model="newCharacter.name"
    @keyup.enter="addNewCharacter"
  />

  <ul v-if="favoriteList.length > 0">
    <li v-for="actor in favoriteList">
      {{ actor.name }}
    </li>
  </ul>
  <p v-else>There are no favorite Characters</p>
</template>
