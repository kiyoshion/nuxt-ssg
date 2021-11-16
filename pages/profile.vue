<template lang="pug">
  .l-container
    .p-content
      .p-content__header
        h1.p-content__ttl 小野田のポートフォリオ。
        p.p-content__desc このサイトはエンジニアである小野田のポートフォリオであり、ブログとそれらに付随する付録的なリファレンスであり、来週には忘れているであろう小野田のための備忘録です。当サイトに記載されている内容は小野田個人の見解であり、所属する団体、全国の小野田さんとは関係ありません。
      .p-content__body
        h2 Blog
        p 小野田が忘れがちなことを小野田にわかりやすくまとめています。
        h2 Work
        p 小野田がローンチしたアプリやサイトです。
        h2 Dev
        p 小野田がやってみたアプリやサイトです。おもにUdemyです。
</template>

<script>
import Meta from '../assets/js/mixin/meta'

export default {
  mixins: [Meta],
  data () {
    return {
      meta: {
        title: 'about',
        description: 'about page',
        type: 'article',
        url: '',
        image: ''
      }
    }
  },
  mounted () {
    this.observerAnime()
  },
  methods: {
    observerAnime () {
      this.$observerAnime(this.$el)
    }
  }
}
</script>
