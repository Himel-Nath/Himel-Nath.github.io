<template>
  <div class="parchment-wrapper">
    <div class="book-theme">
      <h1 class="hidden-text title">The Industry - Cont.</h1>
      <span class="page-number">10</span>
      <figure>
        <video
          src="/canva-ad2.mp4"
          class="canva-ad2"
          muted
          playsinline
          autoplay
          loop
          preload="none"
        ></video>
      </figure>
      <p class="hidden-text page-text full-time-text">
        As he settled into the role, he became a link between departments; coordinating deadlines
        with sales, aligning expectations with QA, and directing DevOps through critical
        deployments. <strong>Over three months, the bug count dropped from 220 to 99.</strong> The
        CEO took notice, publicly recognizing his impact during the company meeting.<br /><br />
        Still not satisfied, he documented a streamlined onboarding process, reducing friction for
        every new developer. Unprompted by management, he also wrote a custom script to automate
        task unassignment, a tool adopted and praised by other managers for its efficiency. He was
        brought into a migration and upgrade project, testing apps, identifying deprecated code, and
        researching safe transitions. Not long after,
        <strong
          >he was promoted to Feature Developer. Now he builds full-stack features. Angular for
          interfaces, PHP and MySQL on the backend. Designing APIs, building dashboards, writing
          client-requested functionality from scratch. Three roles, one year.</strong
        >
      </p>
    </div>
  </div>
</template>

<script setup>
import '@/assets/book-theme.css'
</script>

<style lang="css">
.canva-ad2 {
  float: left;
  height: 22rem;
  margin: 0.5rem;
}
</style>
