<template>
  <section class="container-slug">
    <a-row
      type="flex"
      justifify="start"
      align="bottom"
      class="article-heading"
      :style="`background-image:linear-gradient(to top, rgba(0, 0, 0, 0.65), rgba(0, 0, 0, 0)), url(${article.img})`"
    >
      <a-col class="article-heading_texts">
        <h1>{{ article.title }}</h1>
        <h3 class="description">🧑‍💻 {{ article.description }}</h3>
        <p class="date">
          📅 Actualizado el {{ formatDate(article.updatedAt) }}
        </p>
      </a-col>
    </a-row>

    <article class="container-article">
      <!-- Text -->
      <nuxt-content class="paragraph" :document="article" />

      <a-divider />

      <!-- Prev and Next -->
      <a-row>
        <a-col :span="24">
          <prev-next :prev="prev" :next="next" />
        </a-col>
      </a-row>
    </article>
  </section>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const article = await $content('articles', params.slug).fetch()

    const [prev, next] = await $content('articles')
      .only(['title', 'slug'])
      .sortBy('createdAt', 'asc')
      .surround(params.slug)
      .fetch()

    return {
      article,
      prev,
      next,
    }
  },

  methods: {
    formatDate(date) {
      const options = { year: 'numeric', month: 'long', day: 'numeric' }
      return new Date(date).toLocaleDateString('es', options)
    },
  },

  head() {
    return {
      title: `Marina Suárez 👩‍💻 ${this.article.title}`,
      meta: [
        // hid is used as unique identifier. Do not use `vmid` for it as it will not work
        {
          hid: 'description',
          name: 'description',
          content: this.article.description,
        },
        {
          hid: 'keywords',
          name: 'keywords',
          content: this.article.tags,
        },
        {
          hid: 'author',
          name: 'author',
          content: 'Marina Suárez',
        },
      ],
    }
  },
}
</script>
