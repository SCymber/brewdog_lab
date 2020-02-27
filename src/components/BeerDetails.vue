<template lang="html">
<div v-if="beer" id="beerDetails">
<h2>{{beer.name}}</h2>
<p>Alcohol Percentage: {{beer.abv}}%</p>
<p>Food:</p>
<ul>
<li v-for="food in beer.food_pairing">{{food}}</li>
</ul>
<button v-on:click="addToFavourites">Add To Favourites</button>
</div>
</template>

<script>

import {eventBus} from '../main.js'

export default {
  name: 'beer-details',
  props: ['beer'],
  methods: {
    addToFavourites: function(){
eventBus.$emit('beer-fav', this.beer)
},

}
}

</script>

<style lang="css" scoped>
</style>
