<template lang="pug">
    .home
        h1 My pixel editor WIP
        .pe-config
            label
                input(v-model.number="pixelSide", type="number", min="1", max="5")
                span.pe-config__label Lado del pixel
            label
                input(v-model.number="cols", type="number", min="1", max="40")
                span.pe-config__label Nº columnas
            label
                input(v-model.number="rows", type="number", min="1", max="40")
                span.pe-config__label Nº filas
            label
                input(v-model.number="color", type="color")
                span.pe-config__label Color
            label
                input(v-model="reset", type="checkbox")
                span.pe-config__label Reset
        .pe-editor
            pe-layout(
                :pixelSide="pixelSide",
                :rows="rows",
                :cols="cols",
                :color="color",
                :reset="reset",
                @layout-reset="uncheckReset"
            )
</template>

<script>
import PeLayout from '@/components/pe-layout'
export default {
  name: 'home',
  components: {
    PeLayout
  },
  data () {
    return {
      reset: false,
      pixelSide: 2,
      rows: 10,
      cols: 10,
      color: '#000000'
    }
  },
  methods: {
    uncheckReset () {
      this.reset = false
    }
  }
}
</script>

<style lang="sass">
    .pe-config
        display: flex
        flex-direction: column
        align-items: flex-start

        &__label
            margin-left: 1em
</style>
