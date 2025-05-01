<template>
  <div class="app">
    <div ref="bookContainer" class="book"></div>
  </div>
</template>

<script setup>
import { onMounted, createApp, nextTick, ref } from 'vue'
import { PageFlip } from 'page-flip'

import BookCover from './components/BookCover.vue'
import BookBack from './components/BookBack.vue'
import IntroPage from './components/PageContent/IntroPage.vue'
import SecondPage from './components/PageContent/SecondPage.vue'
import ThirdPage from './components/PageContent/ThirdPage.vue'
import FourthPage from './components/PageContent/FourthPage.vue'

const bookContainer = ref(null)
let pageFlip = null
const pages = [
  { component: BookCover },
  { component: IntroPage },
  { component: SecondPage },
  { component: ThirdPage },
  { component: FourthPage },
  { component: BookBack },
]

onMounted(async () => {
  await nextTick()

  for (const { component } of pages) {
    const wrapper = document.createElement('div')
    wrapper.classList.add('page')
    bookContainer.value.appendChild(wrapper)
    const app = createApp(component)
    app.mount(wrapper)
  }

  pageFlip = new PageFlip(bookContainer.value, {
    width: 400,
    height: 600,
    size: 'fixed',
    showCover: true,
    maxShadowOpacity: 0.5,
    useMouseEvents: true,
    flippingTime: 800,
  })

  pageFlip.loadFromHTML(document.querySelectorAll('.page'))
})
</script>

<style>
.app {
  display: flex;
  justify-content: center;
  align-items: center;
  background: rgb(169, 219, 228);
  height: 100vh;
  width: 100vw;
}
.book {
  width: 800px;
  height: 600px;
}
</style>
