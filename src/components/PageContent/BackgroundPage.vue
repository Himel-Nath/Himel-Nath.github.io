<template>
  <div class="parchment-wrapper">
    <div class="book-theme">
      <h1 class="hidden-text title">What we know</h1>
      <p class="hidden-text page-text intro-text">
        His name is <strong>Himel Dev Nath</strong>. Born in Bangladesh and raised in Oman, his last
        confirmed sighting places him at age 24 in <strong>Halifax, Nova Scotia, Canada</strong>.
        While the details remain sparse, being informed about his background may help infer his
        future whereabouts. According to his family, his relocation to Canada was driven by
        ambition, a desire to pursue higher education and get closer to his ultimate goal. His
        Professors confirm that he not only adapted, but excelled, using his growing knowledge to
        devise projects with unclear purposes (more on his projects in page 5). What complicates his
        profile is his unpredictability - those closest to him cite strong interests in fine arts,
        literature, and video games. While seemingly unrelated, these hobbies hint at a mind that
        refuses to sit still, creatively and geographically. His movements span the Middle East,
        Asia, Europe, and North America. It's anyone's guess where he's headed next.
      </p>
      <img src="/world-map.gif" loading="lazy" alt="world map" class="map" />
    </div>
    <span class="page-number">2</span>
  </div>
</template>

<script setup lang="ts">
import '@/assets/book-theme.css'
</script>

<style lang="css">
.map {
  height: 15rem;
  margin-top: 1rem;
  filter: sepia(100%) brightness(80%);
}

.intro-text {
  column-count: 2;
  column-gap: 0.5em;
}
</style>
