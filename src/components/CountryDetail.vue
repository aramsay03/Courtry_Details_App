<template lang="html">
  <div v-if="country">
    <h3>{{country.name}}</h3>
    <p>Capital: {{country.capital}}</p>
    <p>Population: {{country.population}}</p>
    <p>Languages spoken:</p>
    <ul>
      <li v-for="language in country.languages">{{language.name}}</li>
    </ul>
    <img :src="country.flag" alt="">
  </div>
</template>

<script>
export default {
  name: 'country-details',
  props: ['country']
}
</script>

<style lang="css" scoped>
img {
  max-width: 50%;
}
</style>
