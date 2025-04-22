<template>
    <div class="page">
        <component :is="content"/>
        <div class="navigation">
            <FlipButton label="← Go back" @click="$emit('back')"/>
            <FlipButton label="Flip →" @click="$emit('flip')"/>
        </div>
    </div>
</template>

<script setup>
import FlipButton from './FlipButton.vue';

defineProps(['content'])
</script>

<style scoped>
.page {
  width: 100%;
  height: 100%;
  background-color: antiquewhite;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: transform 0.5s ease;
}

.navigation {
  position: absolute;
  bottom: 10px;
  right: 10px;
  display: flex;
  gap: 10px;
}
</style>