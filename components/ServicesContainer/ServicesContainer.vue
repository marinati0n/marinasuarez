<template>
  <div class="squares-container-container">
    <h3>Puedo ayudarte con</h3>

    <a-row class="squares-container_row" type="flex" justify="space-between">
      <a-col
        v-for="(service, k, i) in services"
        :key="`square-${i}`"
        class="squares-container_col"
        :span="8"
        @click="onSelectSquare(k)"
      >
        <Service
          :title="service.title"
          :description="service.description ? service.description : ''"
        />
      </a-col>
    </a-row>
  </div>
</template>

<script>
// Data
import { services } from '@/utils/services.js'

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
    services,
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
@import './services-container.scss';
</style>
