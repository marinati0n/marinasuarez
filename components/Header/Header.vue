<template>
  <div class="header-container">
    <!-- Social Media -->
    <div class="header_social-media">
      <SocialMedia :align="'right'" />
    </div>

    <!-- Logo -->
    <div class="header_logo">
      <Logo :size="'medium'" />
    </div>
  </div>
</template>

<style lang="scss">
@import '@/assets/scss/main.scss';
@import './header.scss';
</style>
