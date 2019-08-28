<template lang="html">
  <div>
    <label for="country-select">Select a Country</label>
    <select id="country-select" v-model="selectedCountry" @change="handleSelect" >
      <option disabled value="">Select a Country</option>
      <option v-for="(country, index) of countries" :value="country">{{country.name}}</option>
    </select>
    
  </div>
</template>



<script>
import {eventBus} from "../main.js";

export default {
  name: "country-select",
  props: ["countries"],
  data(){
    return {
      selectedCountry: null
    };
  },
  methods: {
    handleSelect(){
      eventBus.$emit("country-selected", this.selectedCountry)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
