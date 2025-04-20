<template>
    <div class="page" @click="$emit('flip')">
        <component :is="content" />
    </div>
</template>

<script setup>
defineProps({
    content: {
        type: Object,    }
})
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
</style>