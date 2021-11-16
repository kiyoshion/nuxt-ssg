<template>
  <div class="mx-auto max-w-2xl my-4">
    <h1>#book</h1>
    <ul>
      <li v-for="(a, i) in articles" :key="i">
        <nuxt-link :to="`/book/${a.slug}`">
          {{ a.title }}
        </nuxt-link>
      </li>
    </ul>
  </div>
</template>

<script>

export default {
  async asyncData ({ $content }) {
    const articles = await $content('book')
      .sortBy('sortNum', 'asc')
      .fetch()

    return {
      articles
    }
  }
}
</script>
