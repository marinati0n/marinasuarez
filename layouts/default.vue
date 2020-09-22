<template>
  <div>
    <a-layout>
      <!-- Header -->
      <a-layout-header id="main-header">
        <Header />
      </a-layout-header>

      <!-- Content -->
      <a-layout-content>
        <Nuxt />
      </a-layout-content>

      <!-- Footer -->
      <a-layout-footer id="main-footer">
        <Footer />
      </a-layout-footer>
    </a-layout>
  </div>
</template>

<style lang="scss">
@import '@/assets/scss/main.scss';
</style>