<template>
  <div id="app">
    <beer-select :beers='beers'></beer-select>
    <beer-details :beer='selectedBeer'></beer-details>
    <beer-fav :favouriteBeers='favouriteBeers'></beer-fav>
  </div>
</template>

<script>
import AllBeers from './components/AllBeers.vue';
import BeerDetails from './components/BeerDetails.vue';
import favouriteBeers from './components/FavouriteBeers.vue';
import {eventBus} from './main.js';

export default {
  name: 'App',
  data(){
    return {
      favouriteBeers: [],
      beers: [],
      selectedBeer: null
    }
  },

  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then(res => res.json())
    .then(data => this.beers = data)

    eventBus.$on('beer-change', (beer) => {
      this.selectedBeer = beer;

    })
    eventBus.$on('beer-fav', (beer) => {
      this.favouriteBeers.push(this.selectedBeer)
    })

  },

methods: {

  },


  components: {
    "beer-select": AllBeers,
    "beer-details": BeerDetails,
    "beer-fav": favouriteBeers
    }
  }
</script>

<style>
/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
</style>
