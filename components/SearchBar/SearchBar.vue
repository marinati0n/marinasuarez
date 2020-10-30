<template>
  <div class="search-bar_container">
    <a-input-search
      v-model="searchQuery"
      placeholder="Buscar artículos..."
      style="width: 200px"
    />

    <a-list
      v-if="articles.length > 0"
      class="found-list"
      item-layout="horizontal"
      :data-source="articles"
    >
      <a-list-item slot="renderItem" slot-scope="item" class="found-item">
        <a-list-item-meta :description="item.description">
          <NuxtLink
            slot="title"
            :to="{ name: 'blog-slug', params: { slug: item.slug } }"
          >
            {{ item.title }}
          </NuxtLink>
        </a-list-item-meta>
      </a-list-item>
    </a-list>
  </div>
</template>

<script>
export default {
  data() {
    return {
      searchQuery: '',
      articles: [],
    }
  },
  watch: {
    async searchQuery(searchQuery) {
      if (!searchQuery) {
        this.articles = []
        return
      }
      this.articles = await this.$content('articles')
        .limit(10)
        .search(searchQuery)
        .fetch()
    },
  },
}
</script>

<style lang="scss">
@import '@/assets/scss/main.scss';
@import './search-bar.scss';
</style>
