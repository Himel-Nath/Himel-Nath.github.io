<script setup lang="ts">
import '@/assets/book-theme.css'
</script>

<template>
  <div class="parchment-wrapper">
    <div class="book-theme">
      <div class="masthead">
        <span class="publication-name">The Shadow Report</span>
        <div class="divider"></div>
        <div class="masthead-sub">
          <span class="date">Wednesday, June 18, 2025</span>
          <span class="volume">Vol. XIII Issue 6</span>
        </div>
        <div class="divider"></div>
      </div>

      <h1 class="title hidden-text">Have you seen this Person?</h1>
      <span class="author">By Unknown Author</span>

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
  box-shadow: 0 0 15px rgba(0, 0, 0, 0.6);
  border: 1px solid #222;
}

.masthead {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.publication-name {
  font-size: 3.4rem;
  font-weight: bold;
}

.masthead-sub {
  width: 95%;
  display: flex;
  justify-content: space-between;
  font-size: 0.85rem;
  color: #333;
  font-style: italic;
}

.divider {
  width: 95%;
  border-top: 1.5px solid black;
  margin: 3px 0 3px 0;
}

.author {
  display: block;
  text-align: left;
  font-style: italic;
  font-size: 0.9rem;
  color: #444;
  padding-left: 10px;
}
</style>
