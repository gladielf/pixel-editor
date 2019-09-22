<template lang="pug">
    .pe-pixel(@click="setPixelColor(color)")
</template>

<script>
export default {
  name: 'pe-pixel',
  props: {
    color: String,
    pixelSide: {
      type: Number,
      default: 1
    },
    reset: Boolean
  },
  watch: {
    pixelSide () {
      this.setPixelSide()
    },
    reset (newValue) {
      if (newValue) {
        this.setPixelColor('#ffffff')
        this.$emit('pixel-reset')
      }
    }
  },
  data () {
    return {
      actualColor: ''
    }
  },
  methods: {
    setPixelSide () {
      this.$el.style.setProperty('--pixel-side', `${this.pixelSide}em`)
    },
    setPixelColor (color) {
      this.actualColor = color
      this.$el.style.setProperty('--pixel-color', `${this.actualColor}`)
    }
  },
  mounted () {
    this.setPixelSide()
  }
}
</script>

<style lang="sass">
    .pe-pixel
        height: var(--pixel-side)
        width: var(--pixel-side)
        box-shadow: inset 0 0 0 1px black
        background-color: var(--pixel-color)
</style>
