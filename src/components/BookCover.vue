<script setup lang="ts">
import FlipButton from './FlipButton.vue';
import '@/assets/book-theme.css';
</script>

<template>
    <div class="book-theme">
        <h1 class="title">My Portfolio</h1>
        <p class="subtitle">Click to open</p>
        <FlipButton label="Flip →" @click="$emit('open')" />
    </div>
</template>