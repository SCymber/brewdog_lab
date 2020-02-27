<template lang="html">
  <div>
    <p>Favourite Beers:</p>
    <ul>
    <li v-for="beer in this.favouriteBeers">{{beer.name}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'beer-fav',
  props: ['favouriteBeers']
}
</script>

<style lang="css" scoped>
</style>
