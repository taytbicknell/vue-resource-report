<template>
  <div class="users-show">
    <div class="container">
        <h2>{{ user.user_name }}</h2>
        <h2>{{ user.email }}</h2>
        <h2>{{ user.primary_zip }}</h2>
        <h2>{{ user.alt_zip }}</h2>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data: function() {
    return {
      user: {}
    };
  },
  created: function() {
      axios.get("http://localhost:3000/api/users/me")
        .then(response => {
          this.user = response.data;
        })
    },
  };
</script>
