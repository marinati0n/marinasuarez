<template>
  <div :class="`social-media-container ${align}`">
    <!-- LinkedIn -->
    <a href="https://www.linkedin.com/in/marina-suarez-fdez/" target="_blank">
      <a-icon type="linkedin" />
    </a>

    <!-- Twitter -->
    <a href="https://twitter.com/Marinati0n" target="_blank">
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
}
</script>

<style lang="scss">
@import '@/assets/scss/main.scss';
@import './socialMedia.scss';
</style>
