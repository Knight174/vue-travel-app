<template>
  <div class="login">
    <h1>Login</h1>
    <div class="form">
      <label for="username">Username</label>
      <input
        v-model="username"
        type="text"
        name="username"
        id="username"
        class="input"
      />
      <label for="password">Password</label>
      <input
        v-model="password"
        type="password"
        name="password"
        id="password"
        class="input"
      />
      <button class="btn" @click="login">Login</button>
    </div>
  </div>
</template>

<script>
import store from "@/store";

export default {
  name: "Login",
  data() {
    return {
      username: null,
      password: null,
    };
  },
  methods: {
    login() {
      // Authenticate against API
      store.user = this.username;
      const redirectPath = this.$route.query.redirect || "/";
      this.$router.push(redirectPath);
    },
  },
};
</script>

<style scoped></style>
