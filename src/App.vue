<template>
  <div id="app">
    <h1>US Zipcode City reverse look up</h1>
    <h5>Powered by Vue.js</h5>
    <ZipInputForm v-on:formSubmit="cityResults" id="form"></ZipInputForm>
    <CityResult v-text="apiResult['place name']"></CityResult>
    <CityResult v-text="apiResult.state"></CityResult>
    <CityResult v-text="apiResult['state abbreviation']"></CityResult>
    <CityResult v-text="apiResult.longitude"></CityResult>
    <CityResult v-text="apiResult.latitude"></CityResult>
  </div>
</template>

<script>
import ZipInputForm from './components/ZipInputForm';
import CityResult from './components/CityResult';

export default {
  name: 'app',
  components: {
    ZipInputForm,
    CityResult
  },
  data: function () {
    return {
      apiResult:''
    }
  },
  methods: {
    cityResults:function(text){
      this.$http.get('http://api.zippopotam.us/us/'+text)
      .then((response) => {
        this.apiResult = response.body.places[0]
      });
    }
  }
}
</script>

<style>

</style>
