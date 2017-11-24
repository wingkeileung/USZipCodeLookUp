<template>
  <div id="app">
    <h1>US Zipcode City reverse look up</h1>
    <h5>Powered by Vue.js</h5>
    <ZipInputForm v-on:formSubmit="cityResults" id="form"></ZipInputForm>
    <CityResults v-text="cityResults"></CityResults>
    <StateResults v-text="stateResults"></StateResults>
  </div>
</template>

<script>
import ZipInputForm from './components/zipInputForm';
import CityResults from './components/cityResults';
import StateResults from './components/stateResults';

export default {
  name: 'app',
  components: {
    ZipInputForm,
    CityResults,
    StateResults
  },
  data: function () {
    return {
      cityResults: '',
      stateResults: ''
    }
  },  
  methods: {
    cityResults:function(zipToSubmit){
      this.$http.get('http://api.zippopotam.us/us/'+zipToSubmit)
      .then((response) => {
        this.cityResults = response.places[0]["place name"];
      });
    },
    stateResults:function(zipToSubmit){
      this.$http.get('http://api.zippopotam.us/us/'+zipToSubmit)
      .then((response) => {
        this.stateResults = response.places[0].state;
      });
    }
  }
}
</script>

<style>
#app {
  
}
</style>
