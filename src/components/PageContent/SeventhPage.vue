<template>
  <div class="parchment-wrapper">
    <div class="book-theme">
      <h1 class="hidden-text title">Early Footprints - Cont.</h1>
      <span class="page-number">8</span>
      <h3 class="hidden-text sub-title">E-Joy Grocery Store (Dated April 2023 - July 2023)</h3>
      <p class="hidden-text page-text">
        During a quieter chapter, he resurfaced behind an unexpected place, behind the counter of a
        grocery store. He rang up groceries, cleaned aisles, dealt with difficult customers. But
        those watching closely saw more. He listened, observed, asked questions, engaged in
        conversation. Face after face, he slowly became someone who could talk to anyone. During the
        slower hours, he turned towards his creative outlet of sketching, hidden behind the
        register. While most would have written the job off, he used it to cultivate his
        interpersonal skills. After four months, he vanished again, this time into something larger;
        a full-time position.
      </p>
      <figure>
        <video
          class="doodles"
          muted
          playsinline
          autoplay
          loop
          src="/doodles.mp4"
          preload="none"
        ></video>
        <figcaption class="caption">Recovered evidence stuffed inside the till drawer.</figcaption>
      </figure>
    </div>
  </div>
</template>

<script setup>
import '@/assets/book-theme.css'
</script>

<style lang="css">
.doodles {
  margin-top: 1rem;
  height: 22rem;
  filter: grayscale(50%);
  box-shadow: 0 0 15px rgba(0, 0, 0, 0.6);
  border: 1px solid #222;
}
</style>
