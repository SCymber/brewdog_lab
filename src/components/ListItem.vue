<template lang="html">
  <li @click="handleChange">{{beer.name}}</li>
</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: 'list-item',
  props: ['beer'],
  methods: {
    handleChange(event){
      eventBus.$emit('beer-change', this.beer)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
