<template>
  <div id="ZipInputForm">
    <form id="zipInput" v-on:submit="formSubmit">
      <input type="text" v-model="zipToSubmit" placeholder="Enter a US valid Zip code...">
      <input type="submit" value="lookup">
    </form>
  </div>
</template>

<script>

export default {
  name: 'ZipInputForm',
  data() {
    return {
      zipToSubmit:''
    }
  },
  methods: {
    formSubmit (e) {
      this.$emit('formSubmit', this.zipToSubmit);
      e.preventDefault();
    }
  }
}
</script>