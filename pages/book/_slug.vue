<template>
  <div class="mx-auto max-w-2xl my-4">
    <div class="mb-8">
      <h1 class="text-3xl mb-8 text-center">
        {{ page.title }}
      </h1>
      <div class="text-gray-400 text-center mb-8">
        <span class="mr-4">作成:{{ $moment(page.createdAt).format('YYYY.MM.DD') }}</span>
        <span>更新:{{ $moment(page.updatedAt).format('YYYY.MM.DD') }}</span>
      </div>
      <p class="text-justify">
        {{ page.description }}
      </p>
    </div>
    <nuxt-content :document="page" />
  </div>
</template>

<script>

export default {
  async asyncData ({ $content, params }) {
    const page = await $content('book', params.slug).fetch()

    return {
      page
    }
  },
  mounted () {
    // this.getEl()
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
