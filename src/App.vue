<template>
  <div class="app">
    <div class="book">
        <BookCover v-if="currentSpread === -1" @open="goToFirstSpread" />
        <div v-else-if="currentSpread < totalSpreads" class="book-spread">
          <Page v-if="leftPage"
            :content="leftPage" 
            side="left"
            @back="goToPreviousSpread"/>
          <Page v-if="rightPage"
            :content="rightPage"
            side="right"
            @flip="goToNextSpread"/>
        </div>
        <BookBack v-else @back="goToPreviousSpread"></BookBack>
    </div>
  </div>
</template>

<script setup>
import { computed, ref } from 'vue'

import BookCover from './components/BookCover.vue'
import Page from './components/Page.vue'   
import BookBack from './components/BookBack.vue'   
import IntroPage from './components/PageContent/IntroPage.vue'
import SecondPage from './components/PageContent/SecondPage.vue'

const currentSpread = ref(-1)
const pages = [IntroPage, SecondPage]
const totalSpreads = Math.ceil(pages.length / 2)

const goToFirstSpread = () => {
  currentSpread.value = 0
}
const goToNextSpread = () => {
  currentSpread.value++  
}

const goToPreviousSpread = () => {
  if (currentSpread.value > 0) {
    currentSpread.value--
  } else {
    currentSpread.value = -1
  }
}

const leftPage = computed(() => pages[currentSpread.value * 2] || null)
const rightPage = computed(() => pages[currentSpread.value * 2 + 1] || null)
</script>

<style scoped>
.app {
  display: flex;
  justify-content: center;
  align-items: center;
  background: rgb(169, 219, 228);  
  height: 100vh;  
  width: 100vw;   
}

.book {
  display: flex; 
  width: 80vw;  
  height: 80vh;  
  background: rgb(169, 219, 228);
  position: relative;
  overflow: hidden;
  justify-content: center; 
}

.book-spread {
  display: flex;
  width: 100%;  
  height: 100%;
}
</style>