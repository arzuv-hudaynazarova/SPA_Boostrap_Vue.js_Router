<template>
  <TheNavigation/>
  <div class="container">

    <router-view v-slot="{Component}" >
      <transition name="moveUp" mode="out-in">
        <component :is="Component" :key="$route.path"></component>
      </transition>
    </router-view>

  </div>
</template>

<script>
import TheNavigation from '@/components/TheNavigation.vue'
export default{
  components: {TheNavigation}
}
</script>

<style lang="css">
.moveUp-enter-active {
  animation: fadeIn 0.5s ease-in-out;
}

@keyframes fadeIn {
  0%, 20% { opacity: 0; transform: translateY(20px); }
  100% { opacity: 1; transform: translateY(0); }
}

.moveUp-leave-active {
  animation: moveUp 0.5s ease-in-out forwards; /* Use 'forwards' to keep the state at the end of the animation */
}

@keyframes moveUp {
  0% { opacity: 1; transform: translateY(0); }
  100% { opacity: 0; transform: translateY(-20px); }
}
</style>
