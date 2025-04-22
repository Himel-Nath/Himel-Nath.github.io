<template>
    <div class="book-theme">
        <component :is="content"/>
        <div class="navigation">
            <FlipButton label="← Go back" @click="$emit('back')"/>
            <FlipButton label="Flip →" @click="$emit('flip')"/>
        </div>
    </div>
</template>

<script setup>
import FlipButton from './FlipButton.vue';
import '@/assets/book-theme.css';

defineProps(['content'])
</script>