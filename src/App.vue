<template>
  <div id="app">
    <h1>Countries:</h1>
    <h4>Select country form list below to see country details.</h4>
    <country-select :countries='countries'></country-select>
    <country-details :country='selectedCountry'></country-details>
  </div>
</template>

<script>
import CountrySelect from './components/CountrySelect.vue';
import CountryDetail from './components/CountryDetail.vue';
import {eventBus} from './main.js';

export default {
  name: 'App',
  data(){
    return {
      countries: [],
      selectedCountry: null
    }
  },
  mounted(){
    fetch('https://restcountries.eu/rest/v2/all')
    .then(res => res.json())
    .then(data => this.countries = data)

    eventBus.$on('country-changed', (country) => {
      this.selectedCountry = country;
    })
  },
  components: {
    "country-select": CountrySelect,
    "country-details": CountryDetail
  }
}
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
</style>
