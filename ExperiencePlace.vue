<template>
  <router-link
      :to="{ name: 'experience.show', params: { experienceSlug: experience.slug } }"
      class="card-link"
  >
    <div class="card">
      <div class="card__image-container">
        <img :src="`/images/${experience.image}`" :alt="experience.name" class="card__image" />
      </div>
      <div class="card__text-container">
        <span class="card__text">
          {{ experience.name }}</span>
      </div>
    </div>
  </router-link>
</template>
<script>
export default {
  props: {
    experience: { type: Object, required: true }
  }
}
</script>

