<script>
// import CharacterFacts from './components/CharacterFacts.vue'
export default {
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
  computed: {
    drinkStaticstics() {
      const drink = ['cosmo', 'soda', 'white russian', 'root beer', 'wine', 'Mt. Dew']
      const staticstics = {
        cosmo: 0,
        soda: 0,
        'white russian': 0,
        'root beer': 0,
        wine: 0,
        'Mt. Dew': 0,
      }
      this.characterList.forEach((character) => {
        drink.forEach((drink) => {
          if (character.drink.indexOf(drink) > -1) {
            staticstics[drink] += 1
          }
        })
      })

      return staticstics
    },
  },
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
<template>
  <h2>The Big Lebowski</h2>
  <h2>Characters</h2>
  <ul>
    <li v-for="(stat, type) in drinkStaticstics">{{ type }}: {{ stat }}</li>
  </ul>
  <ul v-if="characterList.length > 0">
    <li v-for="character in characterList">
      {{ character.name }}
      <button v-on:click="makeFavorite(character)">Favorite</button>
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

  <ul v-if="favoriteCharacter.length > 0">
    <li v-for="actor in favoriteCharacter">
      {{ actor.name }}
    </li>
  </ul>
  <p v-else>There are no favorite Characters</p>
</template>
