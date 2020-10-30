<template>
  <div class="footer-services-container">
    <h4 class="footer-services_title">servicios</h4>

    <ul class="footer-services_list">
      <li
        v-for="(s, k) in subservices"
        :key="k"
        class="footer-services_item-list"
      >
        {{ s.title }}
      </li>
    </ul>
  </div>
</template>

<script>
import { subservices } from '@/utils/subservices'

export default {
  data: () => ({ subservices }),
}
</script>

<style lang="scss">
@import '@/assets/scss/main.scss';
@import './footer-services.scss';
</style>
