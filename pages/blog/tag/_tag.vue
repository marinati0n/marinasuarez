<template>
  <div class="container-blog">
    <!-- Blog header -->
    <a-row class="container-blog_header" type="flex" justify="space-between">
      <a-col class="" :span="12">
        Categorías
        <NuxtLink
          v-for="(cat, i) in categories"
          :key="i"
          :to="`/blog/tag/${cat.slug}`"
        >
          <a-tag class="label-category">{{ cat.emoji }} {{ cat.title }}</a-tag>
        </NuxtLink>

        <NuxtLink :to="'/blog'">
          <a-tag class="label-category">Todos</a-tag>
        </NuxtLink>
      </a-col>

      <a-col class="container-blog_search" :span="12">
        <SearchBar />
      </a-col>
    </a-row>

    <!-- Articles -->
    <a-row class="container-blog__articles" type="flex">
      <a-col
        v-for="article of articles"
        :key="article.slug"
        :span="8"
        class="container-blog__article"
        hoverable
      >
        <NuxtLink :to="{ name: 'blog-slug', params: { slug: article.slug } }">
          <a-card hoverable>
            <!-- Image -->
            <img slot="cover" :alt="article.title" :src="article.img" />

            <!-- Meta -->
            <a-card-meta :title="article.title" class="heading-tertiary">
              <template slot="description">
                <p class="paragraph">
                  {{ article.description }}
                  <a-icon type="caret-right" />
                </p>
              </template>
            </a-card-meta>
          </a-card>
        </NuxtLink>
      </a-col>
    </a-row>
  </div>
</template>

<script>
// Utils
import { categories } from '@/utils/categories.js'

export default {
  async asyncData({ $content, params }) {
    const tags = await $content('tags')
      .where({ slug: { $contains: params.tag } })
      .limit(1)
      .fetch()

    const tag = tags.length > 0 ? tags[0] : {}

    const articles = await $content('articles', params.slug)
      .where({ tags: { $contains: tag.slug } })
      .sortBy('createdAt', 'asc')
      .fetch()

    return {
      articles,
      tag,
    }
  },
  data: () => ({
    categories,
  }),

  /**
   * Metadata
   */
  head() {
    return {
      title: `Marina Suárez | ${this.tag.name}`,
      meta: [
        // hid is used as unique identifier. Do not use `vmid` for it as it will not work
        {
          hid: 'description',
          name: 'description',
          content:
            'Blog de Marina Suárez. 👩‍💻 Información personal y profesional, consejos y herramientas de Marketing Digital.',
        },
      ],
    }
  },
}
</script>
