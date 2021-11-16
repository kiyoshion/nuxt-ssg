<template lang="pug">
  main.mx-auto.max-w-2xl.my-4
    span Hello, I'm Kiyoshi Onoda. I'm a web engineer and developer in Japan.
    span I like watch movies on demand, play video games, and read books.
    span So, I produced some applications based on my hobby. Like this.
</template>

<script>
export default {
  mounted () {
    // this.observerAnime()
  },
  methods: {
    observerAnime () {
      return this.$observerAnime(this.$el)
    }
  }
}
</script>
