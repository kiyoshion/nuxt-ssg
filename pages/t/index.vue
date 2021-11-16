<template lang="pug">
  .l-container
    ul
      li(v-for="(a, i) in articles" :key="i")
        nuxt-link(:to="`/blog/${a.slug}`") {{ a.title }}
</template>

<script>

export default {
  async asyncData ({ $content, params }) {
    const articles = await $content('blog')
      .fetch()

    return {
      articles
    }
  }
}
</script>
