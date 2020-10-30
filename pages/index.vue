<template>
  <div class="home-container">
    <div class="home_projects">
      <MyProjects />
    </div>

    <div class="home-container_squares">
      <ServicesContainer />
      <HomeSubservices />
    </div>
  </div>
</template>

<script>
export default {
  /**
   * Metadata
   */
  head() {
    return {
      title: 'Consultora de Marketing Digital - SEO y Social Media | Marina Suárez',
      meta: [
        // hid is used as unique identifier. Do not use `vmid` for it as it will not work
        {
          hid: 'description',
          name: 'description',
          content:
            'Página web de Marina Suárez, consultora de Marketing Digital 👩‍💻. Profesional especializada en SEO y Social Media para negocios.',
        },
      ],
    }
  },
}
</script>
