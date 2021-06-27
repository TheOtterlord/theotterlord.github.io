<template>
  <div>
    <div class="container">
      <img src="@/assets/img/background.svg" alt="">
      <div class="title">
        <h1>TheOtterlord</h1>
      </div>
    </div>
    <div class="ir-row ir-padding">
      <Project v-for="project in projects" :key="project" :project="project" />
    </div>
  </div>
</template>

<script lang="ts">
import { Vue, Options } from 'vue-class-component'
import Project from '@/components/project.vue'
import projects from '@/assets/json/projects.json'

@Options({
  components: {
    Project
  }
})
export default class Component extends Vue {
  projects!: any[]

  data() {
    return {
      projects: projects.slice(0, 3)
    }
  }
}
</script>

<style scoped>
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
