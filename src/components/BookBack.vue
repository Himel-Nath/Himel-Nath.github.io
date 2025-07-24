<template>
  <div>
    <div class="book-theme">
      <div class="wanted-poster">
        <img src="/wanted.png" alt="mugshot" class="wanted-picture" />
        <div class="resources link-overlay">
          <ul>
            <li><a href="https://github.com/Himel-Nath" target="_blank">Github</a></li>
            <li>
              <a href="https://www.linkedin.com/in/himel-nath/" target="_blank">LinkedIn</a>
            </li>
            <li><a href="/Himel Nath Resume.pdf" target="_blank">Resume</a></li>
            <li><a href="mailto:himelnath6807@gmail.com" target="_blank">Contact</a></li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="css">
.wanted-picture {
  height: 48rem;
}

.wanted-poster {
  position: relative;
  width: 100%;
  max-width: 1000px;
  margin: auto;
}

.link-overlay {
  position: absolute;
  font-family: 'IM-Fell English', serif;
  color: #333;
}

.resources {
  top: 50%;
  left: 15%;

  ul {
    list-style: none;
  }
}

.link-overlay a {
  display: block;
  margin-bottom: 0.3rem;
  text-decoration: none;
}
</style>
