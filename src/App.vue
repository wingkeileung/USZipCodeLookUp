<template>
  <div id="app">
    <h1>US Zipcode City reverse look up</h1>
    <h5>Powered by Vue.js</h5>
    <ZipInputForm v-on:formSubmit="cityResults" id="form"></ZipInputForm>
    <LocationResult v-text="zipToCityResult['place name']"></LocationResult>
    <LocationResult v-text="zipToCityResult.state"></LocationResult>
    <LocationResult v-text="zipToCityResult['state abbreviation']"></LocationResult>
    <LocationResult v-text="zipToCityResult.longitude"></LocationResult>
    <LocationResult v-text="zipToCityResult.latitude"></LocationResult>
    <hr>
    <h1>City to Zip Code Look up</h1>
    <cityStateInputForm v-on:formSubmit="CityStateToZip" id="form"></cityStateInputForm>
    <ZipResult v-text="cityStateToZipResult"></ZipResult>
  </div>
</template>

<script>
import ZipInputForm from './components/ZipInputForm';
import LocationResult from './components/LocationResult';
import CityStateInputForm from './components/CityStateInputForm';
import ZipResult from './components/ZipResult';

export default {
  name: 'app',
  components: {
    ZipInputForm,
    LocationResult,
    CityStateInputForm,
    ZipResult
  },
  data: function () {
    return {
      zipToCityResult:'',
      cityStateToZipResult:''
    }
  },
  methods: {
    cityResults:function(text){
      this.$http.get('http://api.zippopotam.us/us/'+text)
      .then((response) => {
        this.zipToCityResult = response.body.places[0]
      });
    },
    CityStateToZip:function(cityToSubmit, stateToSubmit){
      this.$http.get('http://api.zippopotam.us/US/'+stateToSubmit+'/'+cityToSubmit)
      .then((response) => {
        this.cityStateToZipResult = response.body.places
      });
    }
  }
}
</script>

<style>

</style>
