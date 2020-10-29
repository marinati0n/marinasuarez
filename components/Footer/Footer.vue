<template>
  <div class="footer-container">
    <a-row class="footer-container_row" type="flex" justify="center">
      <a-col class="footer-container_col footer-container_col--2" :span="5">
        <FooterServices />
      </a-col>

      <a-col class="footer-container_col footer-container_col--2" :span="5">
        <FooterLegal />
      </a-col>

      <a-col class="footer-container_col footer-container_col--3" :span="5">
        <FooterContact />

        <a-divider class="footer-divider" />

        <p>Encuéntrame en</p>

        <SocialMedia :align="'center'" />
      </a-col>
    </a-row>

    <a-row type="flex" justify="center">
      <a-col :span="24">
        <FooterCopyright />
      </a-col>
    </a-row>
  </div>
</template>

<style lang="scss">
@import '@/assets/scss/main.scss';
@import './footer.scss';
</style>
