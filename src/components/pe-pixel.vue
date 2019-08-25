<template lang="pug">
    .pe-pixel
</template>

<script>
export default {
  name: 'pe-pixel',
  props: {
    pixelSide: {
      type: Number,
      default: 1
    }
  },
  watch: {
    pixelSide () {
      this.setPixelSide()
    }
  },
  methods: {
    setPixelSide () {
      this.$el.style.setProperty('--pixel-side', `${this.pixelSide}em`)
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
</style>
