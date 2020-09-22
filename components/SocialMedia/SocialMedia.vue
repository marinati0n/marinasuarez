<template>
  <div :class="`social-media-container ${align}`">
    <!-- LinkedIn -->
    <a href="#">
      <a-icon type="linkedin" />
    </a>

    <!-- Twitter -->
    <a href="#">
      <a-icon type="twitter" />
    </a>
  </div>
</template>

<script>
export default {
  props: {
    align: {
      type: String,
      default: 'center',
    },
  },
};
</script>

<style lang="scss">
@import '@/assets/scss/main.scss';
@import './socialMedia.scss';
</style>