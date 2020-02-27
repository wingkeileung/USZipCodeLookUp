<template>
  <div id="CityStateInputForm">
    <form class="form-control col-md-6 mx-auto" style="margin-bottom: 100px;" id="CityStateInput" v-on:submit="formSubmit">
      <div class="row">
        <div class="col">
          <input class="form-control" type="text" v-model="cityToSubmit" placeholder="Enter a US City... e.g. (Seattle)">
            <div class="col-auto">
              <select class="form-control-sm col-md-6" v-model="stateToSubmit">
                <option selected value="">Select the State...</option>
                <option value="AL">Alabama</option>
                <option value="AK">Alaska</option>
                <option value="AZ">Arizona</option>
                <option value="AR">Arkansas</option>
                <option value="CA">California</option>
                <option value="CO">Colorado</option>
                <option value="CT">Connecticut</option>
                <option value="DE">Delaware</option>
                <option value="DC">District of Columbia</option>
                <option value="FL">Florida</option>
                <option value="GA">Georgia</option>
                <option value="HI">Hawaii</option>
                <option value="ID">Idaho</option>
                <option value="IL">Illinois </option>
                <option value="IN">Indiana</option>
                <option value="IA">Iowa</option>
                <option value="KS">Kansas</option>
                <option value="KY">Kentucky</option>
                <option value="LA">Louisiana</option>
                <option value="ME">Maine</option>
                <option value="MD">Maryland</option>
                <option value="MA">Massachusetts</option>
                <option value="MI">Michigan</option>
                <option value="MN">Minnesota</option>
                <option value="MS">Mississippi </option>
                <option value="MO">Missouri</option>
                <option value="MT">Montana</option>
                <option value="NE">Nebraska</option>
                <option value="NV">Nevada</option>
                <option value="NH">New Hampshire</option>
                <option value="NJ">New Jersey</option>
                <option value="NM">New Mexico</option>
                <option value="NY">New York</option>
                <option value="NC">North Carolina</option>
                <option value="ND">North Dakota</option>
                <option value="OH">Ohio</option>
                <option value="OK">Oklahoma</option>
                <option value="OR">Oregon</option>
                <option value="PA">Pennsylvania</option>
                <option value="RI">Rhode Island</option>
                <option value="SC">South Carolina</option>
                <option value="SD">South Dakota</option>
                <option value="TN">Tennessee</option>
                <option value="TX">Texas</option>
                <option value="UT">Utah</option>
                <option value="VT">Vermont</option>
                <option value="VA">Virginia</option>
                <option value="WA">Washington</option>
                <option value="WV">West Virginia</option>
                <option value="WI">Wisconsin</option>
                <option value="WY">Wyoming</option>
              </select>
            </div>
          <input class="btn btn-info btn-sm" type="submit" value="lookup">
          <button class="btn btn-secondary btn-sm" v-on:click="resetFields" type="button">Clear</button>
        </div>
      </div>
    </form>
  </div>
</template>

<script>

export default {
  name: 'CityStateInputForm',
  data () {
    return {
      cityToSubmit:'',
      stateToSubmit:''
    }
  },
  methods: {
    formSubmit (e) {
      this.$emit('formSubmit', this.cityToSubmit, this.stateToSubmit);
      e.preventDefault();
    },
    resetFields (e) {
      this.cityToSubmit = '',
      this.stateToSubmit = ''
      e.preventDefault();
    }
  }
}
</script>

<style>
  #CityStateInput {
    background: Gainsboro
  }
</style>