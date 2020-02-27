<template lang="html">
  <select @change="handleChange">
    <option disabled selected>Select country</option>
    <option v-for="(country, index) in countries" :value="index">{{country.name}}</option>
  </select>
</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: 'country-select',
  props: ['countries'],
  components: {

  },
  methods: {
    // handleChange(){
    //   console.log();
    //   eventBus.$emit('country-changed', this.countries)
    handleChange(event){
      console.log(event.target.value);
      eventBus.$emit('country-changed', this.countries[event.target.value])

    }
  }
}
</script>

<style lang="css" scoped>
</style>
