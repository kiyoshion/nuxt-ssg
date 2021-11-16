<template lang="pug">
  header.mx-auto.max-w-2xl.my-4
    .l-header__inner
      .l-header__logo
        nuxt-link(to="/") norapagos
      .l-header__nav
        GlobalNav
      .l-header__menu
        .c-btn__menu(@click="toggleMenu" :class="{ 'is-active': isMenu }")
          span
          span
          span
</template>

<script>
export default {
  computed: {
    isMenu () {
      return this.$store.state.nav.isMenu
    }
  },
  methods: {
    toggleMenu () {
      this.$store.dispatch('nav/isMenu', !this.$store.state.nav.isMenu)
    }
  }
}
</script>
