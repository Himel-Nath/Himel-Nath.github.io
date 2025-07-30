<template>
  <div class="parchment-wrapper">
    <div class="book-theme">
      <h1 class="hidden-text title">Where it began</h1>
      <blockquote class="page-text hidden-text quote">
        “He was very focused on his future, always studying. He would wake up at 4 a.m. or even pull
        all-nighters.... it was scary”
        <footer>- A close family member</footer>
      </blockquote>
      <p class="hidden-text page-text second-text">
        Some might say he was gifted, but the truth is far more ordinary. In high school, he
        gravitated towards theory heavy subjects like
        <strong>Mathematics and the Sciences</strong>. If something interested him, he'd keep
        chasing it. His final grades, certificates, and offers from top universities across the UK
        and Canada were sufficient evidence for that.
        <strong
          >And yet, he chose Computer Science, something he'd never studied, at Dalhousie
          University.</strong
        >
        To him, it wasn't the end goal. It was the tool. His main challenge in first year wasn't the
        learning curve. It was everything else; living alone, making valuable connections,
        navigating a new environment, and surviving the pandemic. As time progressed, he was exposed
        to complex topics like
        <strong
          >data structures and algorithms, operating systems, and even machine learning.</strong
        >
        <video
          src="/canva-ad.mp4"
          class="canva-ad"
          muted
          playsinline
          autoplay
          loop
          preload="none"
        ></video>
      </p>
    </div>
    <span class="page-number">3</span>
  </div>
</template>

<script setup lang="ts">
import '@/assets/book-theme.css'
</script>

<style lang="css">
.second-text {
  column-count: 2;
  column-gap: 1em;
}

.canva-ad {
  float: right;
  height: 22rem;
  margin: 0.5rem;
}
</style>
