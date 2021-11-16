<template lang="pug">
  .l-container
    h1 #JavaScript
    ul
      li(v-for="(a, i) in articles" :key="i")
        nuxt-link(:to="`/javascript/${a.slug}`") {{ a.title }}
</template>

<script>

export default {
  async asyncData ({ $content }) {
    const articles = await $content('js')
      .sortBy('sortNum', 'asc')
      .fetch()

    return {
      articles
    }
  }
}
</script>
