<template>
  <div class="mx-auto max-w-2xl my-4">
    <h1 class="absolute left-0 ">#Django</h1>
    <ul>
      <li v-for="(a, i) in articles" :key="i">
        <nuxt-link :to="`/django/${a.slug}`">
          {{ a.title }}
        </nuxt-link>
      </li>
    </ul>
  </div>
</template>

<script>

export default {
  async asyncData ({ $content }) {
    const articles = await $content('django')
      .sortBy('sortNum', 'asc')
      .fetch()

    return {
      articles
    }
  }
}
</script>
