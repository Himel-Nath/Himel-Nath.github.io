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
        Some might say he was gifted, but that couldn't be further from the truth. In high school,
        he gravitated towards theory heavy subjects like Mathematics and the Sciences. If something
        interested him, he'd keep chasing it. His final grades, certificate, and offers from top
        universities across UK and Canada were sufficient evidence for that. And yet, he chose
        Computer Science, something he'd never studied, at Dalhousie University. To him, it wasn't
        the end goal. It was the tool. His main challenge in first year wasn't the learning curve.
        It was everything else; living alone, making valuable connections, navigating a new
        environment, and surviving through the pandemic. As time progressed, he was exposed to
        complex topics like data structures and algorithms, operating systems, and even machine
        learning.

        <img src="/canva-ad.gif" alt="advertisement" class="canva-ad" />
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

.quote {
  font-style: italic;
  font-size: 1rem;
  margin: 1rem 0;
  padding-left: 1.5rem;
  border-left: 3px solid #555;
  color: #333;

  footer {
    font-size: 0.9rem;
    font-style: normal;
    margin-top: 0.5rem;
    display: block;
    color: #444;
    text-align: right;
  }
}

.canva-ad {
  float: right;
  height: 350px;
  margin-right: 20px;
}
</style>
