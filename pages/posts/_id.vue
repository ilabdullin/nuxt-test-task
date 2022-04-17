<template>
  <section class="section">
    <div class="container">
      <div class="post__header">
        <nuxt-link class="post_return-link" to="/"
          >вернуться к постам</nuxt-link
        >

        <div class="post__id">Пост {{ post.id }}</div>
      </div>

      <div class="post">
        <img class="post__img" src="https://place-hold.it/650x440" alt="" />

        <div class="post__content">
          <h1 class="post__title">{{ post.title }}</h1>
          <hr />
          <p class="post__text">{{ post.body }}</p>
        </div>
      </div>
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

<style scoped>
.post__header {
  margin-bottom: 24px;
}

.post_return-link {
  font-size: 18px;
  font-weight: 500;
  color: #00dc82;
  transition: all 0.2s ease-in-out;
}

.post_return-link:hover {
  color: #161617;
}

.post__id {
  font-size: 48px;
  font-weight: 700;

  margin-top: 32px;
}

.post {
  display: flex;
  flex-wrap: wrap;
  flex-basis: 100%;
  justify-content: center;
}

.post__img {
  display: block;
  max-width: 100%;
  height: auto;
}

.post__content {
  margin-top: 18px;
}

.post__title::first-letter {
  text-transform: capitalize;
}

.post__text::first-letter {
  text-transform: capitalize;
}
</style>
