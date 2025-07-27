<template>
  <div class="parchment-wrapper">
    <div class="book-theme">
      <span class="page-number">13</span>
      <img src="/abstract.png" alt="abstract art" class="abstract-art" loading="lazy" />
      <h1 class="hidden-text title">The Puzzle Corner</h1>
      <WordSearch />
    </div>
  </div>
</template>

<script setup>
import '@/assets/book-theme.css'
import WordSearch from '../WordSearch.vue'
</script>

<style lang="css">
.abstract-art {
  height: 16rem;
  margin-top: 4rem;
}
</style>
