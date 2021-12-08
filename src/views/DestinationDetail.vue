<template>
  <div>
    <GoBack></GoBack>
    <section class="destination">
      <h1>{{ destination.name }}</h1>
      <div class="destination-detail">
        <img
          :src="require(`@/assets/${destination.image}`)"
          alt="destination.name"
        />
        <p>{{ destination.description }}</p>
      </div>
    </section>
    <!-- nested views -->
    <section class="experiences">
      <h2>Top experience in {{ destination.name }}</h2>
      <div class="cards" id="experience">
        <div
          class="card"
          v-for="experience in destination.experiences"
          :key="experience.slug"
        >
          <router-link
            :to="{
              name: 'ExperienceDetail',
              params: { experienceSlug: experience.slug },
              hash: '#experience',
            }"
          >
            <img
              :src="require(`@/assets/${experience.image}`)"
              :alt="experience.name"
            />
            <span class="card__text">
              {{ experience.name }}
            </span>
          </router-link>
        </div>
      </div>
      <router-view :key="$route.path"></router-view>
    </section>
  </div>
</template>

<script>
import store from "@/store.js";
import GoBack from "@/components/GoBack";

export default {
  name: "DestinationDetail",
  components: {
    GoBack,
  },
  data() {
    return {
      // slug: this.$route.params.slug,
    };
  },
  props: {
    slug: {
      type: String,
      required: true,
    },
  },
  computed: {
    destination() {
      return store.destinations.find(
        (destination) => destination.slug === this.slug
      );
    },
  },
};
</script>

<style scoped>
img {
  max-width: 600px;
  height: auto;
  width: 100%;
  max-height: 400px;
}
.experience {
  padding: 40px 0;
}
.destination-detail {
  display: flex;
  justify-content: space-between;
}
p {
  margin: 0 40px;
  font-size: 20px;
  text-align: left;
}
.cards {
  display: flex;
}
.cards img {
  max-height: 200px;
}
.card {
  padding: 0 20px;
  position: relative;
}
.card__text {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  color: #fff;
  font-size: 25px;
  font-weight: bold;
  text-decoration: none;
}
</style>
