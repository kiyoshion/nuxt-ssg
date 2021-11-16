<template lang="pug">
  .l-container.p-content
    .p-content__header
      h1.p-content__ttl {{ page.title }}
      .p-content__date
        span.p-content__date-created 作成:{{ $moment(page.createdAt).format('YYYY.MM.DD') }}
        span.p-content__date-updated 更新:{{ $moment(page.updatedAt).format('YYYY.MM.DD') }}
      p.p-content__desc {{ page.description }}
    //- .p-content__thumb
    //-   img(:src="require(`~/assets/img/${page.thumbnail}`)")
    .p-content__source(v-if='page.sourceLink')
      .p-content__source-inner
        a.p-content__source-link(:href="`${page.sourceLink}`" target="_blank")
        h3 {{ page.sourceTtl }}
        p {{ page.sourceDesc }}
    //- .p-content__toc.p-toc
    //-   ol.p-toc__list
    //-     li(v-for="link of page.toc" :key="link.id" :class="['p-toc__item', `p-toc__item--${link.depth}`]")
    //-       nuxt-link(:to="`#${link.id}`" class="p-toc__link") {{ link.text }}
    .p-content__body
      nuxt-content(:document="page")
</template>

<script>

export default {
  async asyncData ({ $content, params }) {
    const page = await $content('css', params.slug).fetch()

    return {
      page
    }
  },
  mounted () {
    this.getEl()
    // this.zdogAnime()
  },
  methods: {
    zdogAnime () {
      return this.$zdogAnime(this.$el)
    },
    getEl () {
      const el = this.$el
      /* eslint-disable */
      const h2 = el.querySelectorAll('h2')
      // const p = el.querySelectorAll('p')
      // const img = el.querySelectorAll('img')
      const header = el.querySelector('.p-content__header')
      const callback = function (entries, observer) {
        entries.forEach(entry =>{
          if (entry.isIntersecting) {
            entry.target.classList.add('inview')
          }
        })
      }
      const options = {
        rootMargin: '-150px 0px 0px 0px'
      }
      const io = new IntersectionObserver(callback, options)
      h2.forEach(el => {
        io.observe(el)
      })
      // img.forEach(el => {
      //   io.observe(el)
      // })
      io.observe(header)
      // p.forEach(el => {
      //   io.observe(el)
      // })

    }
  }
}
</script>

<style lang="scss" scoped>
canvas {
  cursor: move;
}
h2 {
  transition: all .4s ease;
  opacity: 0;
  &.inview {
    opacity: 1;
  }
}
.l-container,
.p-content__body {
  p {
    width: 50%;
    text-align: justify;
  }
}

</style>
