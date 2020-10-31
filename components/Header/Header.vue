<template>
  <div class="header-container">
    <a-row type="flex" :justify="'space-between'">
      <a-col class="col-name" :span="6">
        <nuxt-link to="/">
          <h1>Marina Suárez</h1>
        </nuxt-link>
      </a-col>

      <a-col v-if="!visible" class="col-blog" :span="6"
        ><nuxt-link to="/blog"><h2>Blog</h2></nuxt-link></a-col
      >

      <a-col v-if="visible" class="col-social" :span="4"
        ><SocialMedia :align="'right'"
      /></a-col>
    </a-row>

    <a-row v-if="visible" class="row-main-title">
      <a-col class="col-main-title" :span="8">
        <span># No sólo{{ dots }}</span>
        <h2>{{ marketing }}<br />{{ digital }}</h2>
      </a-col>
    </a-row>

    <a-row v-if="visible" type="flex" justify="center">
      <a-col>
        <nuxt-link to="/blog">
          <a-button class="btn-blog" size="large" ghost>Blog</a-button>
        </nuxt-link>
      </a-col>
    </a-row>
  </div>
</template>

<script>
export default {
  data: () => ({
    marketing: 'Marketing',
    digital: 'Digital',
    dots: '',
    i: 0,
    intervalDots: null,
    intervalLetters: null,
    speed: 1000,
  }),
  computed: {
    visible() {
      return this.$route.name === 'index'
    },
  },
  mounted() {
    this.dotsEffect()
    this.lettersEffect()
  },
  beforeDestroy() {
    clearInterval(this.intervalDots)
    clearInterval(this.intervalLetters)
  },
  methods: {
    dotsEffect() {
      this.intervalDots = setInterval(() => {
        if (this.i < 3) {
          this.dots += '.'
          this.i++
        } else {
          this.dots = ''
          this.i = 0
        }
      }, 1250)
    },

    lettersEffect() {
      this.intervalLetters = setInterval(() => {
        const random = Math.floor(Math.random() * 3)

        switch (random) {
          case 0:
            this.marketing.includes('a')
              ? (this.marketing = this.marketing.replace('a', '@'))
              : (this.marketing = this.marketing.replace('@', 'a'))

            break

          case 1:
            this.digital.includes('a')
              ? (this.digital = this.digital.replace('a', '@'))
              : (this.digital = this.digital.replace('@', 'a'))

            this.digital.includes('l')
              ? (this.digital = this.digital.replace('l', '1'))
              : (this.digital = this.digital.replace('1', 'l'))
            break

          case 2:
            this.marketing.includes('e')
              ? (this.marketing = this.marketing.replace('e', '3'))
              : (this.marketing = this.marketing.replace('3', 'e'))
            break
        }
      }, 200)
    },
  },
}
</script>

<style lang="scss">
@import '@/assets/scss/main.scss';
@import './header.scss';
</style>
