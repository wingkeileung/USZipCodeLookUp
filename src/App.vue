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
  </div>
</template>

<script>
import ZipInputForm from './components/ZipInputForm';
import LocationResult from './components/LocationResult';

export default {
  name: 'app',
  components: {
    ZipInputForm,
    LocationResult
  },
  data: function () {
    return {
      zipToCityResult:''
    }
  },
  methods: {
    cityResults:function(text){
      this.$http.get('http://api.zippopotam.us/us/'+text)
      .then((response) => {
        this.zipToCityResult = response.body.places[0]
      });
    }
  }
}
</script>

<style>

</style>
