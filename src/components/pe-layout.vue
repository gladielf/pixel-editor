<template lang="pug">
    .pe-layout
        pe-pixel(v-for="(pixel, index) in totalPixels",
            :key="`pe-pixel-${index}`",
            :color="pixelArray[index]",
            :pixelSide="pixelSide",
            @click.native="setColor(index)")
</template>

<script>
import PePixel from './pe-pixel'
export default {
  name: 'pe-layout',
  components: {
    PePixel
  },
  props: {
    color: String,
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
  data () {
    return {
      pixelArray: []
    }
  },
  watch: {
    pixelSide () {
      this.calculateLayoutWidth()
      this.setPixelArray()
    },
    rows () {
      this.calculateLayoutWidth()
      this.resetPixelArray()
      this.setPixelArray()
    },
    cols () {
      this.calculateLayoutWidth()
      this.resetPixelArray()
      this.setPixelArray()
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
    },
    setColor (index) {
      this.pixelArray.splice(index, 1, this.color)
    },
    setPixelArray () {
      this.pixelArray.length = this.totalPixels
    },
    resetPixelArray () {
      this.pixelArray = []
    }
  },
  mounted () {
    this.setPixelArray()
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
