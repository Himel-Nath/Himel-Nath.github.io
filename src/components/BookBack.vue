<script setup lang="ts">
import FlipButton from './FlipButton.vue';
import '@/assets/book-theme.css';
</script>

<template>
    <div class="book-theme">
        <h1 class="title">The End</h1>
        <p class="subtitle">Thank you for reading!</p>
        <FlipButton label="← Go back" @click="$emit('back')" />
    </div>
</template>
