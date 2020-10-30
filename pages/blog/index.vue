<template>
  <div class="container-blog">
    <!-- Categories -->
    <a-row class="container-blog_header" type="flex" justify="space-between">
      <!-- <a-col class="container-blog_category">Cat 1</a-col>
      <a-col class="container-blog_category">Cat 2</a-col>
      <a-col class="container-blog_category">Cat 3</a-col> -->

      <a-col class="container-blog_title" :span="12">
        <h2>Blog</h2>
      </a-col>

      <a-col class="container-blog_search" :span="12">
        <a-input-search placeholder="input search text" style="width: 200px" />
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
export default {
  async asyncData({ $content, params }) {
    const articles = await $content('articles', params.slug)
      .sortBy('createdAt', 'asc')
      .fetch()

    return {
      articles,
    }
  },

  /**
   * Metadata
   */
  head() {
    return {
      title: 'Blog sobre Marketing Digital - SEO | Marina Suárez',
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
