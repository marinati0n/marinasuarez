<template>
  <div class="contact-form-container">
    <a-row class="contact-form-container_row" type="flex" justify="center">
      <a-col class="contact-form-container_col" :span="8">
        <h3>¿Quieres contactar con nosotros?</h3>
      </a-col>

      <a-col class="contact-form-container_col" :span="8">
        <a-input placeholder="Dinos tu nombre" />
        <a-input placeholder="Dinos tu email" />
        <a-textarea placeholder="¿Qué quieres contarnos?" :rows="4" />
        <a-button type="primary" html-type="submit">Enviar</a-button>
      </a-col>
    </a-row>
  </div>
</template>

<script>
export default {
  name: "ContactForm"
};
</script>

<style lang="scss">
@import "../../assets/scss/main.scss";
@import "./contactForm.scss";
</style>
