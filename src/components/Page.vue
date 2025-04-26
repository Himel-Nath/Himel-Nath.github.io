<template>
    <div class="book-theme">
        <component :is="content"/>
        <div class="navigation">
            <Fold v-if="side==='left'" position="bottom-left" @back="$emit('back')"/>
            <Fold v-if="side==='right'" position="bottom-right" @flip="$emit('flip')"/>
        </div>
    </div>
</template>

<script setup>
import Fold from './Fold.vue';
import '@/assets/book-theme.css';

defineProps({
    content: {
        type: Object,
        required: true
    },
    side: {
        type: String,
        default: 'right'
    },
})
</script>