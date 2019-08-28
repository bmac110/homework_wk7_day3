<template lang="html">
  <div class="">
    <h3>{{country.name}}</h3>
    <p>{{country.capital}}</p>
    <p>{{country.population}}</p>
    <img :src="country.flag">

  </div>
</template>

<script>
export default {
  name: "country-detail",
  props: ["country"]
}
</script>

<style lang="css" scoped>
</style>
