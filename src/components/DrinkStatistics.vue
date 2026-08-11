<script>
export default {
  props: {
    characters: {
      type: Array,
      required: true,
    },
  },
  computed: {
    drinkStatistics() {
      const drink = ['Cosmo', 'soda', 'White Russian', 'root beer', 'wine', 'Mt. Dew']
      const statistics = {
        Cosmo: 0,
        soda: 0,
        'White Russian': 0,
        'root beer': 0,
        wine: 0,
        'Mt. Dew': 0,
      }
      this.characters.forEach((character) => {
        drink.forEach((drink) => {
          if (character.drink.indexOf(drink) > -1) {
            statistics[drink] += 1
          }
        })
      })
      return statistics
    },
  },
}
</script>

<template>
  <h2>Statistics</h2>
  <ul>
    <li v-for="(stat, type) in drinkStatistics">{{ type }}: {{ stat }}</li>
  </ul>
</template>
