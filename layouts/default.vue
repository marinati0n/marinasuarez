<template>
  <div>
    <a-layout>
      <!-- Header -->
      <a-layout-header
        id="main-header"
        :style="this.$route.name === 'index' ? 'height:90vh;' : ''"
      >
        <Header />
      </a-layout-header>

      <!-- Content -->
      <a-layout-content id="main-content">
        <Nuxt />
      </a-layout-content>

      <!-- Footer -->
      <a-layout-footer id="main-footer">
        <Footer />
      </a-layout-footer>
    </a-layout>
  </div>
</template>
