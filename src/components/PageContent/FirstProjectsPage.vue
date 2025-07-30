<template>
  <div class="parchment-wrapper">
    <div class="book-theme">
      <h1 class="hidden-text title">His Creations</h1>
      <h3 class="hidden-text sub-title">Trello Clone (Dated May 2022 - August 2022)</h3>
      <figure>
        <video
          class="trello"
          muted
          playsinline
          autoplay
          loop
          src="/trello.mp4"
          preload="none"
        ></video>
        <figcaption class="caption">
          <a href="https://www.youtube.com/watch?v=2vdi5GXRdnQ" target="_blank"
            >Final prototype shown in Spring 2024.</a
          >
        </figcaption>
      </figure>
      <p class="hidden-text page-text">
        The first signs appeared early. Working with a team of five, he developed a full-stack task
        management system to coordinate group efforts.
        <strong
          >Users could register profiles, create multi-list workflows, assign tasks, and track
          progress in real time.</strong
        >
        Later, outside the confines of academia, he returned to it. Alone. Written in
        <strong>Java (Spring Boot)</strong> and <strong>React</strong>, he stripped out bloat,
        modularized components, and introduced subtle but impactful improvements.
      </p>
      <br />
      <h3 class="hidden-text sub-title">Spotify Automation (Dated - Unknown)</h3>
      <p class="hidden-text page-text">
        Not every build was large. Some were built with purpose. This began as a personal tool, a
        Python script designed to
        <strong>generate Spotify playlists from a single text file.</strong> Without any UI or
        setup, it eliminated the need for manual playlist creation and streamlined a repetitive task
        into a single step. It let users spend less time managing music, and more time listening to
        it.
      </p>
    </div>
    <span class="page-number">5</span>
  </div>
</template>

<script setup>
import '@/assets/book-theme.css'
</script>

<style lang="css">
.trello {
  height: 14rem;
  filter: grayscale(75%);
  box-shadow: 0 0 15px rgba(0, 0, 0, 0.6);
  border: 1px solid #222;
}
</style>
