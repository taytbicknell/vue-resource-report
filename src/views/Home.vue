<template>
  <div class="home">
    <div class="container">
      <h1>{{ message }}</h1>
      <form v-on:submit.prevent="submit()">
        <h1>forecast</h1>
        <ul>
          <li class="text-danger" v-for="error in errors">{{ error }}</li>
        </ul>
        <div class="form-group">
          <label style="color: black">enter zip:</label>
          <input type="zip" class="form-control" v-model="zip">
        </div>
        <input type="submit" class="btn btn-primary" value="submit">
    </form>
   </div>
  </div>
</template>

<style>
</style>

<script>
export default {
  data: function() {
    return {
      message: "Resource Report",
      zip: ""
    };
  },
  created: function() {},
  methods: {
    submit: function() {
   localStorage.setItem("zip", this.zip);
    window.location.href = "/d3index.html"
      } 
  },
  computed: {}
};
</script>