<template>
  <section v-if="experience" class="experience">
    <h1>{{ experience.name }}</h1>
    <GoBack />
    <div class="image-container">
      <img :src="`/images/${experience.image}`" :alt="experience.name" class="experience-image"/>
    </div>
    <p>{{ experience.description }}</p>
  </section>
  <section v-else class="experience-not-found">
    <p>Experience not found.</p>
  </section>
</template>

<script>
import sourceData from '@/data.json';
import GoBack from "@/components/GoBack.vue";

export default {
  components: {GoBack},
  props: {
    experienceSlug: { type: String, required: true }
  },
  computed: {
    experience() {
      const allExperiences = sourceData.destinations.flatMap(
          destination => destination.experiences
      );
      return allExperiences.find(
          experience => experience.slug === this.experienceSlug
      );
    }
  }
};
</script>

<style scoped>
.experience {
  text-align: center;
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
}

h1 {
  font-size: 2.5rem;
  color: #333;
  margin-bottom: 20px;
}

.image-container {
  margin-bottom: 20px;
}

.experience-image {
  max-width: 100%;
  max-height: 400px;
  object-fit: cover;
  border-radius: 8px;
}

p {
  font-size: 1.1rem;
  line-height: 1.6;
  color: #666;
}

.experience-not-found {
  text-align: center;
  color: #900;
  font-size: 1.2rem;
}
</style>
