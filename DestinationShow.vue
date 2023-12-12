<template>
  <div>
    <section v-if="destination" class="destination">
      <h1>{{ destination.name }}</h1>
      <GoBack />
      <div class="destination-details">
        <img :src="`/images/${destination.image}`" :alt="destination.name" />
        <p>{{ destination.description }}</p>
      </div>
    </section>

    <section v-if="destination" class="experiences">
      <h2>Top Experiences in {{ destination.name }}</h2>
      <div class="cards">
        <router-link
            v-for="experience in destination.experiences"
            :key="experience.slug"
            :to="{ name: 'experience.show', params: { experienceSlug: experience.slug } }"
            class="experience-link"
            tag="div"
        >
          <ExperiencePlace
              :experience="experience"
          />
        </router-link>
      </div>
    </section>
  </div>
</template>

<script>
import sourceData from "@/data.json";
import ExperiencePlace from "@/components/ExperiencePlace.vue";
import GoBack from "@/components/GoBack.vue";

export default {
  components: { ExperiencePlace, GoBack },
  props: {
    id: { type: Number, required: true },
  },
  computed: {
    destination() {
      return sourceData.destinations.find(
          destination => destination.id === this.id
      );
    },
  },
};
</script>

<!-- Add any additional styles if necessary -->
<style scoped>
.experience-link {
  text-decoration: none; /* Optional: if you want to remove the underline from links */
}
</style>
