<template>
  <div class="home-container">
    <div class="home-container_squares">
      <SquaresContainer />
    </div>

    <div class="home-container_subservices">
      <HomeServices />
    </div>

    <div class="home-container_sobre-nosotros">
      <HomeSobreNosotros />
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
            'Página web de Marina Suárez (@marinati0n), donde encontrarás información personal, profesional y artículos de marketing digital.',
        },
      ],
    };
  },
};
</script>