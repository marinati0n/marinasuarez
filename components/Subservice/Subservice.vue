<template>
  <div :class="`subservice-container ${selected}`">
    <h3 :class="`subservice-title ${selected}`">
      <a-icon
        v-if="selected !== ''"
        :class="`subservice-icon ${selected}`"
        :type="subservice.iconType"
      />
      {{ subservice.title }}
    </h3>

    <p :class="`subservice-desc ${selected}`">{{ subservice.description }}</p>
  </div>
</template>

<script>
export default {
  props: {
    subservice: {
      type: Object,
      required: true,
      default: () => ({}),
    },
  },
  data: () => ({
    category: {
      type: String,
      default: '',
    },
  }),
  computed: {
    selected() {
      return this.category !== '' && this.category === this.subservice.category
        ? 'selected'
        : ''
    },
  },
  created() {
    window.addEventListener('onSquareSelected', (e) => {
      this.category = e.detail.category
    })
  },
}
</script>

<style lang="scss">
@import '@/assets/scss/main.scss';
@import './subservice.scss';
</style>
