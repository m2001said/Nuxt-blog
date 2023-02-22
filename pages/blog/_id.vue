<template>
  <div>
    <h1>{{ $store.state.selectedPost.title }}</h1>
    <p>{{ $store.state.selectedPost.body }}</p>
  </div>
</template>

<script>
export default {
  head() {
    return {
      title: this.$store.state.selectedPost.title,
    }
  },
  fetch({ $axios, store, params }) {
    // if this selectedPost is here so don't fetch it, and make sure of this id that it equal to the params id
    if (store.state.selectedPost && store.state.selectedPost.id == params.id)
      return true
    return $axios.$get(`/posts/${params.id}`).then((res) => {
      store.commit('updateSelectedPost', res)
    })
  },
}
</script>
