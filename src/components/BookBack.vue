<script setup lang="ts">
import FlipButton from './FlipButton.vue';
</script>

<template>
    <div class="book-back">
        <h1 class="title">The End</h1>
        <p class="subtitle">Thank you for reading!</p>
        <FlipButton label="← Go back" @click="$emit('back')" />
    </div>
</template>

<style scoped>
.book-back {
  width: 100%;
  height: 100%;
  background: linear-gradient(to left, #f5f5dc, #e6ddc4); /* soft paper look */
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  color: #333;
  font-family: 'Georgia', serif;
  padding: 20px;
  box-sizing: border-box;
  text-align: center;
}
</style>