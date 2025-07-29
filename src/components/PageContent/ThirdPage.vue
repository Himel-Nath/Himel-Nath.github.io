<template>
  <div class="parchment-wrapper">
    <div class="book-theme">
      <h1 class="hidden-text title">Where it began - Cont.</h1>
      <figure>
        <img src="/award.jpg" alt="award" class="award" loading="lazy" />
        <figcaption class="caption">
          Bruce and Dorothy Rossetti Scholarship - Gold Award, 2022.
        </figcaption>
      </figure>
      <p class="hidden-text page-text third-text">
        His Professors and Dean took notice of his performance, awarding him the
        <strong>Sexton Scholar</strong> designation multiple times for maintaining a
        <strong>GPA above 3.85.</strong> Shown here is a certificate recognizing him for the
        <strong>highest CGPA</strong> in his cohort. Final year allowed him to explore different
        realms by choosing Network Security, Cloud Computing and Cryptography as his electives. He
        graduated with a <strong>certificate in Cybersecurity</strong> to complement his degree. But
        that wasn't all. When others chose easy electives, he pursued a
        <strong>minor in Mathematics</strong>. Courses like Advanced Linear Algebra, Ordinary
        Differential Equations, and Multivariable Calculus fed a passion he never let go of. His
        academic record closed with a <strong>CGPA of 4.16</strong> despite not having written a
        single line of code before University. If that doesn't make him dangerous, it makes him
        unpredicatable. And in this case, that might be worse.
      </p>
    </div>
    <span class="page-number">4</span>
  </div>
</template>

<script setup>
import '@/assets/book-theme.css'
</script>

<style lang="css">
.award {
  height: 220px;
  width: 400px;
  box-shadow: 0 0 15px rgba(0, 0, 0, 0.6);
  border: 1px solid #222;
}

.third-text {
  column-count: 2;
  column-gap: 1em;
}
</style>
