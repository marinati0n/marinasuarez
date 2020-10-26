<template>
  <img :class="`logo-img ${size}`" src="" alt="Marina Suárez Fernández" />
</template>

<script>
export default {
  props: {
    size: {
      type: String,
      default: 'medium',
    },
  },
}
</script>

<style lang="scss">
@import '@/assets/scss/main.scss';
@import './logo.scss';
</style>
