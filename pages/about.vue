<template lang="pug">
  .l-container
    h1.p-ttl ノラでパゴるメディア - 個人開発者のこれまでとこれから
    p このサイトはエンジニアである高浜きょんし(<a href="https://twitter.com/kiyoshion" target="_blank">@kiyoshion</a>)の技術ブログです。来週には忘れているであろう高浜にむけて書いた備忘録です。当サイトに記載されている内容は高浜個人の見解であり、所属する団体、全国の高浜さんとは一切関係ありません。
    h2 Blog
    p 小野田が忘れがちなことをJKにわかりやすくまとめています。
    h2 Work
    p 小野田がローンチしたアプリやサイトやツールです。
    h2 Dev
    p 小野田がやってみたアプリやサイトやツールです。おもにUdemyやUdemyなどです。
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
  }
}
</script>
