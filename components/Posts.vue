<template>
  <section class="posts">
    <div class="container">
      <h1 class="posts__title">Nuxt blog</h1>

      <div class="post__card">
        <div class="post__card-col" v-for="post of posts" :key="post.id">
          <div class="card">
            <a class="card__link" href="#" @click.prevent="openPost(post)">
              <img
                class="card__img"
                src="https://place-hold.it/370x300"
                alt=""
              />
              <div class="card__content">
                <h2 class="card__title">{{ post.title }}</h2>
                <div class="card__description">
                  {{ post.body }}
                </div>
              </div>
            </a>
          </div>
        </div>
      </div>
      <!-- /.post__card -->
    </div>
    <!-- /.container -->
  </section>
  <!-- /.posts -->
</template>

<script>
export default {
  async asyncData({ $axios }) {
    const posts = await $axios.$get(
      'https://jsonplaceholder.typicode.com/posts'
    );
    return { posts };
  },

  data: () => ({
    posts: [],
  }),

  async mounted() {
    this.posts = await this.$axios.$get(
      'https://jsonplaceholder.typicode.com/posts'
    );
  },

  methods: {
    openPost(post) {
      this.$router.push('/posts/' + post.id);
    },
  },
};
</script>

<style scoped>
.posts {
  margin: 2.8rem 0;
}

.posts__title {
  font-size: 48px;
  margin-bottom: 24px;
}

.post__card {
  display: flex;
  flex-wrap: wrap;
  margin: 0 -1rem 2.8rem;
}

.post__card-col {
  flex-basis: 33.33333%;
  padding: 1rem;
}

@media (max-width: 767px) {
  .post__card-col {
    flex-basis: 50%;
  }
}

@media (max-width: 565px) {
  .post__card-col {
    flex-basis: 100%;
  }
}

.card {
  overflow: hidden;
  cursor: pointer;

  border-radius: 10px;
  box-shadow: 0 0 4px rgba(0, 0, 0, 0.25);

  transition: box-shadow 0.2s linear;
}

.card:hover {
  box-shadow: 0 0 25px rgba(0, 0, 0, 0.25);
}

.card__img {
  display: block;
  max-width: 100%;
  height: auto;
}

.card__content {
  padding: 1rem 0.8rem;
}

.card__title {
  display: flex;
  justify-content: space-between;

  font-size: 1.06rem;

  text-transform: uppercase;
  font-weight: 700;

  margin-bottom: 8px;
}

@media (max-width: 767px) {
  .card {
    max-width: 370px;
  }
}

@media (max-width: 565px) {
  .card {
    margin: 0 auto;
  }
}
</style>
