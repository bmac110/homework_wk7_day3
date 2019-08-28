<template lang="html">
  <div class="">
    <h1>Countries of the World!!!</h1>
    <country-select :countries="countries"></country-select>
    <country-detail v-if="selectedCountry" :country="selectedCountry"></country-detail>
    <!-- <div class="main-container">
      <label for="country-select">Select a Country</label>
      <select id="country-select" v-model="selectedCountry" >
        <option disabled value="">Select a Country</option>
        <option v-for="country in countries" :value="country">{{country.name}}</option>
      </select>
      </div>
        <country-list :countries='countries'></country-list> -->



  </div>
</template>

<script>
// import CountryList from './components/CountryList.vue';
import CountryDetail from './components/CountryDetail.vue';
import CountrySelect from './components/CountrySelect.vue';
import {eventBus} from './main.js';

export default {
  name: 'app',
  data(){
    return {
      countries: [],
      selectedCountry: null
    };
  },
  mounted(){
    fetch('https://restcountries.eu/rest/v2/all')
    .then(res => res.json())
    .then(countries => this.countries = countries)



    eventBus.$on("country-selected", (country) => {
      this.selectedCountry = country;
    })
  },

  components: {
    // "country-list": CountryList,
    "country-detail": CountryDetail,
    "country-select": CountrySelect
  }
}
</script>

<style lang="css" scoped>
.main-container {
  display: flex;
  justify-content: space-around;
}
</style>
