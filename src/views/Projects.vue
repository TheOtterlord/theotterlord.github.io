<template>
  <div class="projects">
    <div class="ir-row ir-padding">
      <div class="ir-col l4 m6 s12 ir-padding" v-for="project in projects" :key="project" >
        <ProjectCard :project="project" />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Vue, Options } from 'vue-class-component'
import ProjectCard from '@/components/ProjectCard.vue'
import projects from '@/assets/json/projects.json'

@Options({
  components: {
    ProjectCard
  }
})
export default class Component extends Vue {
  projects!: any[]

  data() {
    return {
      projects
    }
  }
}
</script>

<style scoped>
.projects {
  margin-top: 128px;
}

img {
  width: 100%;
  height: 100vh;
}

.container {
  position: relative;
  text-align: center;
  color: white;
}

.title {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-family: 'Brush Script MT', cursive;
  font-size: 1.5em;
  color: var(--secondary);
}
</style>
