<template>
  <div class="squares-container-container">
    <h3>Nuestros servicios</h3>

    <a-row class="squares-container_row" type="flex" justify="center">
      <a-col
        v-for="(square, k, i) in squares"
        :key="`square-${i}`"
        class="squares-container_col"
        :span="4"
        :style="style"
        @click="onSelectSquare(k)"
      >
        <Square :title="square.title" :description="square.description ? square.description : ''" />
      </a-col>
    </a-row>
  </div>
</template>

<script>
// Data
import { squares } from '@/utils/squares.js';

export default {
  data: () => ({
    columnHeight: {
      type: Number,
      default: 0,
    },
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
  computed: {
    style() {
      return `height: ${this.columnHeight}px`;
    },
  },
  methods: {
    calcColumnHeight() {
      this.columnHeight = document.querySelector(
        '.squares-container_col'
      ).clientWidth;
    },
    onSelectSquare(category) {
      if (category !== this.customEventData.category) {
        this.customEventData = { category: category };
      } else {
        this.customEventData = { category: '' };
      }

      this.customEvent = new CustomEvent('onSquareSelected', {
        detail: this.customEventData,
      });
      window.dispatchEvent(this.customEvent);
    },
  },
  mounted() {
    this.calcColumnHeight();
  },
};
</script>

<style lang="scss">
@import '@/assets/scss/main.scss';
@import './squaresContainer.scss';
</style>
