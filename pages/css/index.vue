<template lang="pug">
  .l-container
    h1 #CSS
    ul
      li(v-for="(a, i) in articles" :key="i")
        nuxt-link(:to="`/css/${a.slug}`") {{ a.title }}
</template>

<script>

export default {
  async asyncData ({ $content }) {
    const articles = await $content('css')
      .sortBy('sortNum', 'asc')
      .fetch()

    return {
      articles
    }
  }
}
</script>
