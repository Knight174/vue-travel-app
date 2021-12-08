<template>
  <nav>
    <h1>Vue Travel App</h1>
    <router-link to="/">Home</router-link>
    <!-- <router-link to="/brazil">Brazil</router-link>
    <router-link to="/panama">Panama</router-link>
    <router-link to="/hawaii">Hawaii</router-link>
    <router-link to="/jamaica">Jamaica</router-link> -->
    <router-link
      v-for="destination in destinations"
      :key="destination.id"
      :to="{ name: 'DestinationDetail', params: { slug: destination.slug } }"
    >
      {{ destination.name }}
    </router-link>
    <router-link to="/user">Dashboard</router-link>
  </nav>
</template>

<script>
import store from "@/store";
export default {
  name: "Navigation",
  data() {
    return {
      destinations: store.destinations,
    };
  },
};
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
nav {
  display: flex;
  height: 45px;
  line-height: 45px;
  padding-left: 30px;
  padding-right: 30px;
  align-items: center;
  position: sticky;
  top: 0;
  border-bottom: 1px solid grey;
  background-color: #fff;
  z-index: 1;
}
nav h1 {
  margin-right: 30px;
}
nav a {
  font-weight: bold;
  color: #2c3e50;
  margin-right: 30px;
}

/* nav a.router-link-exact-active {
  color: #825;
} */

nav a.my-link-active-class {
  color: #abcdef;
}
</style>
