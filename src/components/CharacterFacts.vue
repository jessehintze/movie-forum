<script>
export default {
  props: {
    characters: {
      type: Array,
      required: true
    },
  },
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
}
</script>

<template>
  <h2>Characters</h2>
  <ul>
    <li v-for="(stat, type) in drinkStaticstics" :key="`drink-${stat}-${type}`">
      {{ stat }}: {{ type }}
    </li>
  </ul>
  <ul v-if="characterList.length > 0">
    <li v-for="(character, index) in characterList" :key="`character-${index}`">
      {{ character.name }}
      <button v-on:click="makeFavorite(character)">Favorite</button>
    </li>
  </ul>
  <p v-else>There are no characters</p>
  <p>Enter your favorite character</p>
  <pre>
  {{ newCharacter }}
  </pre>
  <input
    type="text"
    placeholder="Enter Character"
    v-model="newCharacter.name"
    @keyup.enter="addNewCharacter"
  />
</template>
