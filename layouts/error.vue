<template>
  <section class="section">
    <h1 class="error__title">Error 404</h1>

    <nuxt-link class="error__link" to="/">вернуться к постам</nuxt-link>
  </section>
</template>

<script>
export default {};
</script>

<style scoped>
.section {
  width: 600px;
  margin: 0 auto;
  padding-top: 5rem;
}

.error__title {
  font-size: 64px;
  color: red;
}

.error__link {
  font-size: 24px;
  text-decoration: underline;
  transition: all 0.2s ease-in-out;
}

.error__link:hover {
  color: #00dc82;
}
</style>
