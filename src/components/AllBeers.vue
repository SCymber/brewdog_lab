<template lang="html">
<div>
<ul>
<li v-for="(beer, index) in beers" :beer="beer" :key="index">{{beer.name}}</li>
</ul>

</div>
</template>

<script>
export default {
  name: 'beer-select',
  props: ['beers'],

}

</script>

<style lang="css" scoped>
</style>
