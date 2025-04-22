<script setup lang="ts">
import FlipButton from './FlipButton.vue';
</script>

<template>
    <div class="book-cover">
        <h1 class="title">My Portfolio</h1>
        <p class="subtitle">Click to open</p>
        <FlipButton label="Flip →" @click="$emit('open')" />
    </div>
</template>
  
<style scoped>
  .book-cover {
    width: 100%;
    height: 100%;
    background: linear-gradient(to right, #a1c4fd, #c2e9fb); 
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    cursor: pointer;
    transition: transform 0.3s ease;
  }
  
  .book-cover:hover {
    transform: scale(1.02);
  }
  
  .title {
    font-size: 2em;
    font-weight: bold;
    color: #003366;
  }
  
  .subtitle {
    font-size: 1em;
    color: #444;
  }
</style>
  