<template>
  <div class="account-container">
    <h1>Account</h1>
    <img src="/images/ibiza.jpg" alt="Account Photo" class="account-photo"/>
    <GoBack />
  </div>
</template>
<style>
.account-container {
  text-align: center;
  margin-top: 20px;
}
.account-photo {
  width: 150px;
  height: 150px;
  border-radius: 80%;
  margin-bottom: 18%;
}
</style>
<script setup>
import GoBack from "@/components/GoBack.vue";
</script>
