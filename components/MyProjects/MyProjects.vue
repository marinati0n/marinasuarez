<template>
  <div class="my-projects_container">
    <h3>Proyectos</h3>

    <a-row class="my-projects_row" type="flex" justify="center">
      <a-col
        v-for="(project, k, i) in myProjects"
        :key="`project-${i}`"
        class="my-projects_col"
        :span="5"
      >
        <a :href="project.link" target="_blank">
          <img :src="project.logo" :alt="project.title" />
        </a>

        <h4 class="project-job">· {{ project.job }} ·</h4>
      </a-col>
    </a-row>
  </div>
</template>

<script>
// Data
import { myProjects } from '@/utils/my-projects.js'

export default {
  data: () => ({
    myProjects,
  }),
}
</script>

<style lang="scss">
@import '@/assets/scss/main.scss';
@import './my-projects.scss';
</style>
