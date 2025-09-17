<script setup lang="ts">
import FastFetch from "./components/FastFetch.vue"
</script>

<template>
  <div class="page-container">
    <section class="main-section">
      <picture>
        <img src="./assets/pictures/profile-photo.png" alt="">
      </picture>
      <FastFetch />
    </section>
    <section class="about"></section>
    <section class="skills"></section>
    <section class="projects"></section>
    <section class="social"></section>
  </div>
</template>

<style scoped lang="scss">
.page-container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.main-section {
  padding: 20px;
  margin: 20px;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  gap: 2rem;
  border: 1px solid var(--vt-c-accent-blue);
  width: fit-content;
  border-radius: 24px;
  img {
    width: 200px;
    height: 200px;
    margin: 20px;
  }
}
</style>
