<template>
  <div class="forecast">
    <div class="container">
      <form v-on:submit.prevent="submit()">
        <h1>forecast</h1>
        <ul>
          <li class="text-danger" v-for="error in errors">{{ error }}</li>
        </ul>
        <div class="form-group">
          <label>primary zip:</label>
          <input type="primary_zip" class="form-control" v-model="primary_zip">
        </div>
        <input type="submit" class="btn btn-primary" value="submit">
      </form>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      primary_zip: "",
      errors: []
    };
  },
  methods: {
    submit: function() {
      var params = {
        primary_zip: this.primary_zip
      };
      axios
        .post("http://localhost:3000/api/forecasts", params)
        .then(response => {
          this.$router.push("/forecasts");
        })
        .catch(error => {
          this.errors = error.response.data.errors;
        });
    }
  }
};
</script>
