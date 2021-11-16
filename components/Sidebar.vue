<template lang="pug">
  nav.l-sidebar(:class="{ 'is-active': isMenu }" @click="toggleMenu")
    .l-sidebar__inner
      ul.l-sidebar__list
        li.l-sidebar__item(v-for="(link, i) in links" :key="i")
          nuxt-link.l-sidebar__link(:to="link.val") {{ link.name }}
</template>

<script>
export default {
  data () {
    return {
      links: [
        { name: 'Django', sub: 'What I did', val: '/django' },
        { name: 'Tips', sub: 'What I did', val: '/tips' },
        { name: 'Series', sub: 'What I tried', val: '/series' },
        { name: 'Reference', sub: 'What I think', val: '/refs' },
        { name: 'blog', sub: 'What I think', val: '/blog' },
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
