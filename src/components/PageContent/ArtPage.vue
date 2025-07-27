<template>
  <div class="parchment-wrapper">
    <div class="book-theme">
      <h1 class="hidden-text title">The Gallery</h1>
      <span class="page-number">12</span>
      <img src="/sketches.png" alt="portfolio sketches" class="sketches" loading="lazy" />
    </div>
  </div>
</template>

<script setup>
import '@/assets/book-theme.css'
</script>

<style lang="css">
.sketches {
  height: 42rem;
}
</style>
