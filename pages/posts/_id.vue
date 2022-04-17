<template>
  <section class="section">
    <div class="container">
      <h1>{{ post.title }}</h1>

      <hr />

      <h3>{{ post.body }}</h3>
    </div>
  </section>
</template>

<script>
export default {
  validate({ params }) {
    return /^\d+$/.test(params.id);
  },

  async asyncData({ $axios, params }) {
    const post = await $axios.$get(
      'https://jsonplaceholder.typicode.com/posts/' + params.id
    );
    return { post };
  },
};
</script>

<style></style>
