<template>
  <div class="container">
    <div>
      <logo />
      
      <h1 class="title">{{ title }}</h1>
      <h2 class="subtitle">{{ subtitle }}</h2>
      
      <div class="links">
        <nuxt-link
          v-for="post in posts"
          :to="{name: 'posts-id', params: {id: post.id}}"
          :key="post.id"
          class="button--grey"
        >
          {{ post.title }}
        </nuxt-link>
      </div>

    </div>
  </div>
</template>

<script>
import Logo from '~/components/Logo.vue'

export default {
  components: {
    Logo
  },
  data() {
    return {
      title: 'nuxt-fundamentals',
      subtitle: 'My reveting Nuxt.js project'
    }
  },
  head() {
    return {
      title: 'Homepage',
      meta: [
        { name: 'twitter:title', content: 'Nuxtjs fundamentals' },
        { name: 'twitter:description', content: 'WeichieProjects' },
        { name: 'twitter:image', content: '/logo.png' },
        { name: 'twitter:card', content: 'summary_large_image' }
      ]
    }
  },
  computed: {
    posts() {
      return this.$store.state.posts.all;
    }
  }
}
</script>

<style scoped>
  .container {
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
  }
  .title {
    font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
    display: block;
    font-weight: 300;
    font-size: 100px;
    letter-spacing: 1px;
  }
  .subtitle {
    font-weight: 300;
    font-size: 42px;
    color: #526488;
    word-spacing: 5px;
  }
  .links {
    padding-top: 15px;
  }
</style>
