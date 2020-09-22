<template>
  <div class="square-container">
    <div class="square-container_texts">
      <h2>{{ title }}</h2>
      <p v-if="description !== ''">{{ description }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      default: '',
    },

    description: {
      type: String,
      default: '',
    },
  },
};
</script>

<style lang="scss">
@import '@/assets/scss/main.scss';
@import './square.scss';
</style>
