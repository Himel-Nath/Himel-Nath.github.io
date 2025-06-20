<script setup lang="ts">
import '@/assets/book-theme.css'
</script>

<template>
  <div class="parchment-wrapper">
    <div class="book-theme">
      <h1 class="title hidden-text">Have you seen this person?</h1>

      <figure class="image-container">
        <img src="/cover.gif" alt="cover photo" class="cover-photo" />
        <figcaption class="caption">Captured somewhere in Europe, 2024.</figcaption>
      </figure>

      <p class="hidden-text page-text">
        Strange signs of activity have surfaced; peculiar inventions, cryptic sketches and a digital
        footprint across the web. Some believe he could be scheming his next big move. In response
        to the growing interest, our reporters have compiled everything known about the individual
        in question. From early origins to current whereabouts, and theories about what may come
        next. The truth, as always, lies between the lines.
      </p>
    </div>
  </div>
</template>

<style lang="css">
.image-container {
  float: right;
  margin: 0.5em 1em 0.5em 1em;
  text-align: center;
}

.cover-photo {
  height: 450px;
  filter: grayscale(1) contrast(1.2);
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.6);
}

.caption {
  font-size: 0.75rem;
  font-style: italic;
  color: #444;
  margin-top: 0.3em;
}

p::first-letter {
  font-size: 200%;
  font-weight: bold;
  float: left;
  margin-right: 6px;
  line-height: 1;
}
</style>
