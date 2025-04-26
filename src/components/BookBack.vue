<script setup lang="ts">
import Fold from './Fold.vue';
import '@/assets/book-theme.css';
</script>

<template>
    <div class="book-theme">
        <h1 class="title">The End</h1>
        <p class="subtitle">Thank you for reading!</p>
        <Fold position="bottom-left" @click="$emit('back')" />
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