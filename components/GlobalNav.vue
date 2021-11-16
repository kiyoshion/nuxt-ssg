<template lang="pug">
  nav.mx-auto.max-w-2xl.my-4(:class="{ 'is-active': isMenu }" @click="toggleMenu")
    ul.flex
      li(v-for="(link, i) in links" :key="i")
        nuxt-link(:to="link.val") {{ link.name }}
</template>

<script>
export default {
  data () {
    return {
      links: [
        { name: 'Django', sub: 'What I did', val: '/django' },
        { name: 'JavaScript', sub: 'What I did', val: '/javascript' },
        { name: 'FastAPI', sub: 'What I did', val: '/fastapi' },
        { name: 'CSS', sub: 'What I did', val: '/css' },
        { name: 'Series', sub: 'What I tried', val: '/series' },
        { name: 'Reference', sub: 'What I think', val: '/refs' },
        { name: 'blog', sub: 'What I think', val: '/blog' },
        { name: 'book', sub: 'What I think', val: '/book' },
        { name: 'About', sub: 'Who is Onoda', val: '/about' }
      ]
    }
  },
  computed: {
    isMenu () {
      return this.$store.state.nav.isMenu
    }
  },
  mouted () {
    // this.setNoise()
  },
  methods: {
    toggleMenu () {
      this.$store.dispatch('nav/isMenu', false)
    }
  }
}
</script>
