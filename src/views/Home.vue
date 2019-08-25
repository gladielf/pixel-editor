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
        .pe-editor
            pe-layout(
                :pixelSide="pixelSide",
                :rows="rows",
                :cols="cols"
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
      pixelSide: 1,
      rows: 10,
      cols: 10
    }
  }
}
</script>

<style lang="sass">
    .pe-config
        display: flex
        flex-wrap: wrap
        width: 12em

        &__label
            margin-left: 1em
</style>
