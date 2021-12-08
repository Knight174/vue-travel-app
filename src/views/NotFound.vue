<template>
  <div class="not-found">
    <h1>Not Found</h1>
    <p>
      We couldn't find that page. Try going
      <router-link :to="{ name: 'Home' }">Home</router-link>
    </p>
  </div>
</template>

<script>
export default {
  name: "NotFound",
};
</script>

<style scoped></style>
