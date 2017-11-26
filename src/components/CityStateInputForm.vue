<template>
  <div id="CityStateInputForm">
    <form id="CityStateInput" v-on:submit="formSubmit">
      <input type="text" v-model="cityToSubmit" placeholder="Enter a US City... e.g. (Seattle)">
      <input type="text" v-model="stateToSubmit" placeholder="Enter the City State abbreviation... (e.g. WA)">
      <input type="submit" value="lookup">
    </form>
  </div>
</template>

<script>

export default {
  name: 'CityStateInputForm',
  data() {
    return {
      cityToSubmit:'',
      stateToSubmit:''
    }
  },
  methods: {
    formSubmit (e) {
      this.$emit('formSubmit', this.cityToSubmit, this.stateToSubmit);
      e.preventDefault();
    }
  }
}
</script>