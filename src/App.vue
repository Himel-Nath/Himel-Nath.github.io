<template>
  <div>
    <audio ref="backgroundAudio" src="/audio.mp3" loop preload="none"></audio>
    <audio ref="flipAudio" src="/flip.mp3" preload="auto"></audio>
    <div>
      <video
        ref="lightMode"
        autoplay
        loop
        muted
        playsinline="true"
        class="background"
        :class="{ visible: currentMode === 'lumos' }"
        preload="none"
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
        preload="none"
      >
        <source src="/rain.mp4" type="video/mp4" />
      </video>
    </div>
    <div class="overlay" @click="toggleVisibility"></div>
    <div class="app">
      <div ref="bookContainer" class="book-container" :class="{ hidden: !bookVisible }"></div>
      <button class="toggle-button" @click="toggleDisplay">
        {{ currentMode === 'lumos' ? '🔅' : '🌙' }}
      </button>
      <button class="toggle-button mute" @click="toggleMute">
        {{ isMuted ? '🔇' : '🔊' }}
      </button>
    </div>
  </div>
</template>

<script setup>
import { onMounted, createApp, nextTick, ref } from 'vue'
import { PageFlip } from 'page-flip'

import BookCover from './components/BookCover.vue'
import BookBack from './components/BookBack.vue'
import BackgroundPage from './components/PageContent/BackgroundPage.vue'
import EducationPage from './components/PageContent/EducationPage.vue'
import DegreePage from './components/PageContent/DegreePage.vue'
import FirstProjectsPage from './components/PageContent/FirstProjectsPage.vue'
import SecondProjectsPage from './components/PageContent/SecondProjectsPage.vue'
import InternshipPage from './components/PageContent/InternshipPage.vue'
import RetailPage from './components/PageContent/RetailPage.vue'
import FirstFulltimePage from './components/PageContent/FirstFulltimePage.vue'
import SecondFulltimePage from './components/PageContent/SecondFulltimePage.vue'
import HobbiesPage from './components/PageContent/HobbiesPage.vue'
import ArtPage from './components/PageContent/ArtPage.vue'
import InteractivePage from './components/PageContent/InteractivePage.vue'

const bookContainer = ref(null)
let pageFlip = null
const currentMode = ref('lumos')
const backgroundAudio = ref(null)
const isMuted = ref(true)
const bookVisible = ref(true)
const flipAudio = ref(null)
const pages = [
  { component: BookCover },
  { component: BackgroundPage },
  { component: EducationPage },
  { component: DegreePage },
  { component: FirstProjectsPage },
  { component: SecondProjectsPage },
  { component: InternshipPage },
  { component: RetailPage },
  { component: FirstFulltimePage },
  { component: SecondFulltimePage },
  { component: HobbiesPage },
  { component: ArtPage },
  { component: InteractivePage },
  { component: BookBack },
]

function toggleDisplay() {
  currentMode.value = currentMode.value === 'lumos' ? 'nox' : 'lumos'
  showSpell(currentMode.value)
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
  const spell = isMuted.value ? 'muffliato' : 'sonorus'
  showSpell(spell)
}

function toggleVisibility() {
  bookVisible.value = !bookVisible.value
  const spell = bookVisible.value ? 'revelio' : 'evanesco'
  showSpell(spell)
}

const loadPages = () =>
  new Promise((resolve) => {
    const checkPage = () => {
      const pages = document.querySelectorAll('.page')
      if (pages.length > 0) resolve()
      else requestAnimationFrame(checkPage)
    }
    checkPage()
  })

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
    width: 575,
    height: 775,
    size: 'fixed',
    showCover: true,
    maxShadowOpacity: 0,
    useMouseEvents: true,
    flippingTime: 800,
  })

  window.addEventListener('load', async () => {
    await loadPages()
    pageFlip.loadFromHTML(document.querySelectorAll('.page'))
  })

  // initial reveal
  setTimeout(() => {
    requestAnimationFrame(() => {
      revealText()
    })
  }, 300)

  // add page flip sound
  pageFlip.on('changeState', (e) => {
    if (e.data === 'user_fold' || e.data === 'flipping') {
      const sound = flipAudio.value
      if (sound) {
        sound.volume = 0.5
        sound.currentTime = 0
        sound.play().catch((error) => {
          console.error('Error playing flip sound:', error)
        })
      }
    }
  })

  // reveal text effect on each flip
  pageFlip.on('flip', () => {
    requestAnimationFrame(() => {
      revealText()
    })
  })

  // custom cursor
  const wandCursor = document.createElement('div')
  wandCursor.className = 'wand-cursor'
  wandCursor.innerHTML = `
    <img src='/wand.png'>
    <div class='glow'></div>
  `
  document.body.appendChild(wandCursor)
  const glow = wandCursor.querySelector('.glow')
  glow.style.display = 'none'

  document.addEventListener('mousemove', (e) => {
    wandCursor.style.top = `${e.clientY}px`
    wandCursor.style.left = `${e.clientX}px`
  })

  // glow effect on hover
  document.addEventListener('mouseover', (e) => {
    glow.style.display = e.target.closest('button, a, [role="button"], .clickable')
      ? 'block'
      : 'none'
  })

  const spellText = document.createElement('div')
  spellText.className = 'spell-text'
  wandCursor.appendChild(spellText)

  document.addEventListener('keydown', handleKeydown)
})

// text effect on page flip
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

// wobbly spell effect
function showSpell(word) {
  const text = document.querySelector('.spell-text')
  text.innerHTML = ''
  const letters = word.split('')

  letters.forEach((char, index) => {
    const span = document.createElement('span')
    span.className = 'spell-char'
    span.textContent = char
    span.style.setProperty('--wobble-amount', `${Math.random() * 6 - 2}px`)
    text.appendChild(span)

    setTimeout(() => {
      span.style.opacity = '1'
    }, index * 200)
  })

  setTimeout(
    () => {
      letters.forEach((_, index) => {
        setTimeout(() => {
          if (text.children[index]) {
            text.children[index].style.opacity = '0'
          }
        }, index * 200)
      })
    },
    letters.length * 150 + 1000,
  )
}

// keyboard navigation
function handleKeydown(e) {
  if (!pageFlip) {
    return
  }

  switch (e.key) {
    case 'ArrowLeft':
      pageFlip.flipPrev()
      break
    case 'ArrowRight':
      pageFlip.flipNext()
      break
    case 'ArrowUp':
      if (!bookVisible.value) {
        toggleVisibility()
      }
      break
    case 'ArrowDown':
      if (bookVisible.value) {
        toggleVisibility()
      }
      break
    case 'l':
    case 'L':
      toggleDisplay()
      break
    case 'm':
    case 'M':
      toggleMute()
      break
  }
}
</script>

<style lang="css">
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
  left: 1rem;
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

.spell-text {
  position: absolute;
  top: -1.5rem;
  left: 25%;
  transform: translateX(-50%);
  font-family: 'IM Fell English SC', serif;
  color: gold;
  font-size: 1.5rem;
  pointer-events: none;
  display: flex;
  gap: 0.1rem;
  white-space: nowrap;
}
.spell-char {
  opacity: 0;
  animation: wobble 1s infinite ease-in-out;
  transform: translateY(0);
}

@keyframes wobble {
  0%,
  100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(var(--wobble-amount, 2px));
  }
}
</style>
