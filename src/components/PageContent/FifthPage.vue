<template>
  <div class="parchment-wrapper">
    <div class="book-theme">
      <h1 class="hidden-text title">His Creations - Cont.</h1>
      <h3 class="hidden-text sub-title">Discord Bot (Dated January 2023 - April 2023)</h3>
      <figure class="footage">
        <video
          class="discord"
          muted
          playsinline
          autoplay
          loop
          src="/discord.mp4"
          preload="none"
        ></video>
        <figcaption class="caption">
          <a href="https://www.youtube.com/watch?v=Elgp9GkWQOE" target="_blank"
            >Footage captured some time in 2023.</a
          >
        </figcaption>
      </figure>

      <p class="hidden-text page-text">
        This bot appeared without fanfare but it quickly made noise. Its users could
        <strong
          >track real-time game discounts, manage wishlists, check hours played, leave reviews, and
          get live updates on the latest games releasing.</strong
        >
        The idea was simple: give gamers more control over their time, their spending, their
        backlog. Footage of the bot in action began circulating, submitted by loyal users who relied
        on it for months. Forensic scientists later uncovered the framework behind it:
        <strong>Python</strong>, working in tandem with <strong>AWS Lambda</strong>,
        <strong>Dynamo DB</strong>, <strong>EventBridge</strong>, <strong>S3</strong>, and
        <strong>EC2</strong>.
      </p>
      <br />
      <h3 class="hidden-text sub-title">The Daily Portfolio (May 2025 - )</h3>
      <p class="hidden-text page-text">
        Even after entering the workforce (see page 9), he didn't stop. Few have seen it in full.
        Those who have say it was built with <strong>Vue</strong> and handcrafted with care. A site
        like this, immersive, responsive, and full of subtle interactivity, could be dangerous in
        the wrong hands. Our editors were unable to secure live footage, but witnesses speak of
        <strong
          >glowing cursors, moving images, and a layout that doesn't behave like normal
          websites.</strong
        >
      </p>
    </div>
    <span class="page-number">6</span>
  </div>
</template>

<script setup>
import '@/assets/book-theme.css'
</script>

<style lang="css">
.discord {
  height: 225px;
  filter: grayscale(75%);
  box-shadow: 0 0 15px rgba(0, 0, 0, 0.6);
  border: 1px solid #222;
  margin: 0 1rem 0 1rem;
}

.footage {
  float: right;
}
</style>
