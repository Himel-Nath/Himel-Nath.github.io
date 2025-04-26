<script setup lang="ts">
import Fold from './Fold.vue';
import '@/assets/book-theme.css';
</script>

<template>
    <div class="book-theme">
        <h1 class="title">My Portfolio</h1>
        <p class="subtitle">Click to open</p>
        <Fold position="bottom-right" @click="$emit('open')" />
    </div>
</template>

<style scoped>
.book-theme {
    width: 40vw;  
    height: 80vh; 
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    background-color: #f5f5dc; 
    position: relative;  
    margin: 0 auto; 
}
</style>