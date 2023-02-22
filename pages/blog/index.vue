<template>
  <div class="blogs flex">
    <div
      class="blog flex-column"
      v-for="post in $store.state.posts"
      :key="post.id"
    >
      <h3>
        <nuxt-link :to="`/blog/${post.id}`">
          <!-- we make span because nuxt-link will not allow onclick to be made -->
          <span @click="updateSelectedPost(post)">
            {{ post.title }}
          </span>
        </nuxt-link>
      </h3>
      <p>{{ post.body }}</p>
    </div>
  </div>
</template>

<script>
export default {
  fetch({ $axios, store }) {
    return $axios.$get('/posts').then((res) => {
      store.commit('updatePosts', res)
    })
  },
  methods: {
    // this function to push the date to the store and it will not call the api unless you refresh the page
    updateSelectedPost(post) {
      this.$store.commit('updateSelectedPost', post)
    },
  },
}
</script>

<style>
.blogs {
  flex-wrap: wrap;
  margin: 2rem;
  gap: 1rem;
}
.blog {
  background: var(--primary-light);
  width: 300px;
  text-align: center;
  border: solid 1px var(--black);
}
.blog h3 {
  margin: 0;
  border-bottom: solid 1px var(--black);
  width: 100%;

  padding: 1rem 0;
  background: var(--primary);
  height: 80px;
}
.blog p {
  height: 120px;
  padding: 1rem;
}
</style>
