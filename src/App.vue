<template>
  <div class="book">
      <BookCover v-if="currentPage === -1" @open="goToFirstPage" />
      <Page v-else-if="currentPage < pages.length"
      :content="pages[currentPage]" 
      @flip="goToNextPage" 
      @back="goToPreviousPage"/>
      <BookBack v-else @back="goToPreviousPage"></BookBack>
  </div>
</template>

<script setup>
import { ref } from 'vue'

import BookCover from './components/BookCover.vue'
import Page from './components/Page.vue'   
import BookBack from './components/BookBack.vue'   
import IntroPage from './components/PageContent/IntroPage.vue'
import SecondPage from './components/PageContent/SecondPage.vue'

const currentPage = ref(-1)
const pages = [IntroPage, SecondPage]

const goToFirstPage = () => {
  currentPage.value = 0
}
const goToNextPage = () => {
  currentPage.value++  
}

const goToPreviousPage = () => {
  if (currentPage.value > 0) {
    currentPage.value--
  } else {
    currentPage.value = -1
  }
}
</script>

<style scoped>
.book {
width: 60vw;
height: 80vh;
margin: 50px auto;
border: 2px solid #ccc;
box-shadow: 0 0 20px rgba(0,0,0,0.1);
background: beige;
position: relative;
overflow: hidden;
}
</style>