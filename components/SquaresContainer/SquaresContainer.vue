<template>
  <div class="squares-container-container">
    <h3>Puedo ayudarte con</h3>

    <a-row class="squares-container_row" type="flex" justify="space-between">
      <a-col
        v-for="(square, k, i) in squares"
        :key="`square-${i}`"
        class="squares-container_col"
        :span="8"
        @click="onSelectSquare(k)"
      >
        <Square
          :title="square.title"
          :description="square.description ? square.description : ''"
        />
      </a-col>
    </a-row>
  </div>
</template>

<script>
// Data
import { squares } from '@/utils/squares.js'

export default {
  data: () => ({
    customEvent: {
      type: CustomEvent,
      default: undefined,
    },
    customEventData: {
      type: Object,
      default: {},
    },
    squares,
  }),
  methods: {
    onSelectSquare(category) {
      if (category !== this.customEventData.category) {
        this.customEventData = { category }
      } else {
        this.customEventData = { category: '' }
      }

      this.customEvent = new CustomEvent('onSquareSelected', {
        detail: this.customEventData,
      })
      window.dispatchEvent(this.customEvent)
    },
  },
}
</script>

<style lang="scss">
@import '@/assets/scss/main.scss';
@import './squaresContainer.scss';
</style>
