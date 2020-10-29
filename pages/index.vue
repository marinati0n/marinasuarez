<template>
  <div class="home-container">
    <div class="home_projects">
      <MyProjects />
    </div>

    <div class="home-container_squares">
      <SquaresContainer />

      <HomeServices />
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
      title: 'Marina Suárez 👩‍💻 SEO & Social Media',
      meta: [
        // hid is used as unique identifier. Do not use `vmid` for it as it will not work
        {
          hid: 'description',
          name: 'description',
          content:
            'Página web de Marina Suárez, donde encontrarás información personal, profesional y artículos de marketing digital.',
        },
      ],
    }
  },
}
</script>
