<template>
    <button class="flip-button">
        {{ label }}
    </button>
</template>

<script setup>
defineProps({
    label: {
        type: String,
    }
})
</script>

<style scoped>
.flip-button {
  background: none;
  border: none;
  color: #003366;
  font-size: 1em;
  cursor: pointer;
  padding: 0.5em;
}

.flip-button:hover {
  color: #0055aa;
  text-decoration: none;
}
</style>