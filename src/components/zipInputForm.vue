<template>
  <div id="ZipInputForm">
    <form class="form-control col-md-6 mx-auto" id="zipInput" style="margin-bottom: 50px" v-on:submit="formSubmit">
      <input class="form-control" type="text" v-model="zipToSubmit" placeholder="Enter a US valid Zip code...">
      <input class="btn btn-info btn-sm" type="submit" value="lookup">
      <button class="btn btn-secondary btn-sm" v-on:click="resetFields" type="button">Clear</button>
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
    },
    resetFields (e) {
      this.zipToSubmit = '',
      e.preventDefault();
    }
  }
}
</script>

<style>
#zipInput {
  background: Gainsboro
}
</style>