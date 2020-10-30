<template>
  <div class="home-services-container">
    <a-row class="home-services_row" type="flex" justify="center">
      <a-col
        v-for="(subservice, i) in subservices"
        :key="`subservice-${i}`"
        :span="8"
        class="home-services_col"
      >
        <Subservice :subservice="subservice" />
      </a-col>
    </a-row>
  </div>
</template>

<script>
// Data
import { subservices } from '@/utils/subservices.js'

export default {
  data: () => ({
    subservices,
  }),
}
</script>

<style lang="scss">
@import '@/assets/scss/main.scss';
@import './home-subservices.scss';
</style>
