<template>
  <div id="nav">
    <AppLink id="logo" to="/">Travel's Trail</AppLink>
    <AppLink
        v-for="destination in destinations"
        :key="destination.id"
        :to="{name: 'destination.show', params:{id: destination.id, slug: destination.slug}}"
    >
      {{ destination.name }}
    </AppLink>
    <AppLink :to="{name: 'protected'}">Panel</AppLink>
  </div>
</template>
<script>
import sourceData from '@/data.json'
export default {
  data(){
    return {
      destinations: sourceData.destinations
    }
  }
}
</script>
