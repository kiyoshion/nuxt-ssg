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
        { name: 'Home', sub: "Hi, it's me", val: '/' },
        { name: 'Prod', sub: 'What I did', val: '/prod' },
        { name: 'Dev', sub: 'What I tried', val: '/dev' },
        { name: 'Blog', sub: 'What I think', val: '/blog' },
        { name: 'Plofile', sub: 'Who is Onoda', val: '/profile' }
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
    },
    setNoise () {
      const canvas = this.$el.querySelector('canvas')
      /* eslint-disable */
      const ctx = canvas.getContext('2d')
      // const w = ctx.canvas.width
      // const h = ctx.canvas.height
      const w = 480
      const h = 270
      console.log('hello canvas', canvas, w, h)

      const rgb = {
        r: 150,
        g: 150,
        b: 150
      }
      const idata = ctx.createImageData(w, h)
      const data = idata.data
      const dotAlpha = 40

      const x = w / 2
      const y = h / 2
      const radius = Math.sqrt(Math.pow(x, 2) + Math.pow(y, 2)) | 0
      // let grad = ctx.createRadialGradient(x, y, 0, x, y, radius)
      const blend = 'screen'

      const draw = {
        noise () {
          for (let i = 0, l = data.length; i < l; i += 4) {
            data[i + 0] = rgb.r
            data[i + 1] = rgb.g
            data[i + 2] = rgb.b
            data[i + 3] = Math.random() * dotAlpha | 0;
          }
          ctx.putImageData(idata, 0, 0)
        },
        grad () {
          grad = ctx.createRadialGradient(x, y, 0, x, y, radius)
          grad.addColorStop(0, 'rgba(0,0,0,0)')
          grad.addColorStop(1, 'rgba(0,0,0,1)')
        },
        render () {
          ctx.clearRect(0, 0, w, h)
          this.noise()

          ctx.beginPath()
          // ctx.fillStyle = grad
          ctx.rect(0, 0, w, h)
          ctx.fill()
          requestAnimationFrame(this.render.bind(this))
        },
        initialize () {
          ctx.globalCompositeOperation = blend
          // this.grad()
          this.render()
        }
      }
      draw.initialize()
    }
  },
  watch: {
    isMenu () {
      if (this.isMenu) {
        this.setNoise()
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.l-nav--noise {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 1;
  canvas {
    width: 100%;
    height: 100%;
    // background-image: url('/img/book-shelf.png');
    background-image: none;
    // background-color: rgba(150, 150, 150, .5);
    // background-color: #ececec;
    background-position: 0 0;
    background-size: cover;
  }
}
.l-nav__inner {
  z-index: 2;
  background-color: rgba(0, 0, 0, 0);
}
.l-nav__link {
  color: #393939;
  &:hover {
    color: #eee;
    transition: color .2s ease-out;
  }
}
</style>
