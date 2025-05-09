<template>
  <div>
    <audio ref="backgroundAudio" src="/audio.mp3" loop></audio>
    <div>
      <video
        ref="lightMode"
        autoplay
        loop
        muted
        playsinline="true"
        class="background"
        :class="{ visible: currentMode === 'lumos' }"
      >
        <source src="/fireplace.mp4" type="video/mp4" />
      </video>
      <video
        ref="darkMode"
        autoplay
        loop
        muted
        playsinline="true"
        class="background"
        :class="{ visible: currentMode === 'nox' }"
      >
        <source src="/rain.mp4" type="video/mp4" />
      </video>
    </div>
    <div class="overlay" @click="toggleVisibility"></div>
    <div class="app">
      <div ref="bookContainer" class="book-container" :class="{ hidden: !bookVisible }"></div>
      <button class="toggle-button" @click="toggleDisplay">
        {{ currentMode === 'lumos' ? '🌙' : '🔅' }}
      </button>
      <button class="toggle-button mute" @click="toggleMute">
        {{ isMuted ? '🔊' : '🔇' }}
      </button>
    </div>
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
const currentMode = ref('lumos')
const backgroundAudio = ref(null)
const isMuted = ref(true)
const bookVisible = ref(true)
const pages = [
  { component: BookCover },
  { component: IntroPage },
  { component: SecondPage },
  { component: ThirdPage },
  { component: FourthPage },
  { component: BookBack },
]

function toggleDisplay() {
  currentMode.value = currentMode.value === 'lumos' ? 'nox' : 'lumos'
}

function toggleMute() {
  isMuted.value = !isMuted.value
  const audio = backgroundAudio.value
  if (audio) {
    audio.muted = isMuted.value
    if (!isMuted.value) {
      audio.play().catch((error) => {
        console.error('Error playing audio:', error)
      })
    }
  }
}

function toggleVisibility() {
  bookVisible.value = !bookVisible.value
}

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
    width: 550,
    height: 750,
    size: 'fixed',
    showCover: true,
    maxShadowOpacity: 0,
    useMouseEvents: true,
    flippingTime: 800,
  })

  pageFlip.loadFromHTML(document.querySelectorAll('.page'))

  // initial reveal
  setTimeout(() => {
    revealText()
  }, 100)

  // reveal on each flip
  pageFlip.on('flip', () => {
    requestAnimationFrame(() => {
      revealText()
    })
  })
})

function revealText() {
  const pages = [...document.querySelectorAll('.page')].filter((el) => el.offsetParent !== null)

  pages.forEach((currentPage) => {
    const elements = currentPage.querySelectorAll('.hidden-text')

    elements.forEach((element) => {
      element.classList.remove('reveal-text')
      void element.offsetWidth
      element.classList.remove('hidden-text')
      element.classList.add('reveal-text')
    })
  })
}
</script>

<style>
.app {
  display: flex;
  justify-content: center;
  align-items: center;
  background: transparent;
  height: 100vh;
  width: 100vw;
}
.overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 1;
  background: transparent;
}
.book-container {
  width: 1200px;
  height: 750px;
  transition:
    transform 1s ease-in-out,
    opacity 1s ease-in-out;
  transform: translateY(0);
  opacity: 1;
  pointer-events: auto;
  z-index: 2;
}
.book-container.hidden {
  transform: translateY(700px);
  opacity: 1;
  pointer-events: none;
}
.toggle-button {
  position: fixed;
  bottom: 1rem;
  right: 1rem;
  z-index: 10;
  background: rgba(255, 255, 255, 0.6);
  border: none;
  border-radius: 50%;
  padding: 0.5rem;
  cursor: pointer;
  transition: background 0.3s ease;
}

.toggle-button:hover {
  background: rgba(255, 255, 255, 0.9);
}

.toggle-button.mute {
  bottom: 4rem;
}
</style>
