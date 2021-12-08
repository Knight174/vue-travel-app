<template>
  <div>
    <h1>User {{ user }}</h1>
    <p>
      <router-link :to="{ name: 'Invoices' }">Invoices</router-link>
    </p>
    <button @click="logOut" class="btn">Log out</button>
  </div>
</template>

<script>
import store from "@/store";

export default {
  name: "User",
  data() {
    return {
      user: store.user,
    };
  },
  methods: {
    logOut() {
      store.user = null;
      this.$router.push("/");
    },
  },
};
</script>

<style scoped></style>
