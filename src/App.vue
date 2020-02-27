<template>
  <div id="app">
    <beer-select :beers='beers'></beer-select>
    <beer-details :beer='selectedBeer'></beer-details>
  </div>
</template>

<script>
import AllBeers from './components/AllBeers.vue';
import BeerDetails from './components/BeerDetails.vue';
import {eventBus} from './main.js';

export default {
  name: 'App',
  data(){
    return {
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
  },
  components: {
    "beer-select": AllBeers,
    "beer-details": BeerDetails
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
