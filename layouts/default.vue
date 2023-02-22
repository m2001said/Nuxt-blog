<template>
  <div>
    <nav class="flex">
      <nuxt-link to="/">Home</nuxt-link>
      <nuxt-link to="/blog">Blogs</nuxt-link>
    </nav>

    <Nuxt />

    <footer>@copy right 2023</footer>
  </div>
</template>

<style>
:root {
  --primary: rgb(78, 219, 184);
  --primary-light: rgb(220, 247, 240);
  --black: black;
  --white: white;
  --gray: rgb(211, 210, 210);
}
body {
  margin: 0;
}
.flex,
.flex-column {
  display: flex;
  align-items: center;
  justify-content: center;
}
.flex-column {
  flex-direction: column;
}
nav {
  gap: 2rem;
  background: black;
}
nav a {
  color: white;
  font-size: 1.4rem;
  padding: 1rem;
  text-decoration: none;
  transition: all 0.3s;
}
nav a:hover {
  color: var(--primary);
}
.nuxt-link-exact-active {
  color: var(--primary);
}

footer {
  background: black;
  color: white;
  text-align: center;
  padding: 1rem;
}
</style>
