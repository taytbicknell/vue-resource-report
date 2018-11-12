<template>
  <div class="signup">
    <div class="container">
      <form v-on:submit.prevent="submit()">
        <h1>signup</h1>
        <ul>
          <li class="text-danger" v-for="error in errors">{{ error }}</li>
        </ul>
        <div class="form-group">
          <label>user name:</label> 
          <input type="text" class="form-control" v-model="user_name">
        </div>
        <div class="form-group">
          <label>email:</label>
          <input type="email" class="form-control" v-model="email">
        </div>
        <div class="form-group">
          <label>primary zip:</label>
          <input type="primary_zip" class="form-control" v-model="primary_zip">
        </div>
        <div class="form-group">
          <label>alt zip:</label>
          <input type="alt_zip" class="form-control" v-model="alt_zip">
        </div>
        <div class="form-group">
          <label>password:</label>
          <input type="password" class="form-control" v-model="password">
        </div>
        <div class="form-group">
          <label>password confirmation:</label>
          <input type="password" class="form-control" v-model="passwordConfirmation">
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
      user_name: "",
      email: "",
      primary_zip: "",
      alt_zip: "",
      password: "",
      passwordConfirmation: "",
      errors: []
    };
  },
  methods: {
    submit: function() {
      var params = {
        user_name: this.user_name,
        email: this.email,
        alt_zip: this.alt_zip,
        primary_zip: this.primary_zip,
        password: this.password,
        password_confirmation: this.passwordConfirmation
      };
      axios
        .post("http://localhost:3000/api/users", params)
        .then(response => {
          this.$router.push("/login");
        })
        .catch(error => {
          this.errors = error.response.data.errors;
        });
    }
  }
};
</script>
