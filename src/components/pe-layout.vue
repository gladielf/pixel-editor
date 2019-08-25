<template lang="pug">
    .pe-layout
        pe-pixel(v-for="(pixel, index) in totalPixels",
            :key="`pe-pixel-${index}`",
            :pixelSide="pixelSide")
</template>

<script>
import PePixel from './pe-pixel'
export default {
  name: 'pe-layout',
  components: {
    PePixel
  },
  props: {
    pixelSide: {
      type: Number,
      default: 1
    },
    rows: {
      type: Number,
      default: 10
    },
    cols: {
      type: Number,
      default: 10
    }
  },
  watch: {
    pixelSide () {
      this.calculateLayoutWidth()
    },
    rows () {
      this.calculateLayoutWidth()
    },
    cols () {
      this.calculateLayoutWidth()
    }
  },
  computed: {
    totalPixels () {
      return this.rows * this.cols
    }
  },
  methods: {
    calculateLayoutWidth () {
      const width = this.cols * this.pixelSide
      this.$el.style.setProperty('--layout-width', `${width}em`)
    }
  },
  mounted () {
    this.calculateLayoutWidth()
  }
}
</script>

<style lang="sass">
    .pe-layout
        width: var(--layout-width)
        display: flex
        flex-wrap: wrap
</style>
