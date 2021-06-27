<template>
  <div class="project">
    <img :src="project.image" alt="" />
    <div class="ir-padding">
      <h2>{{ project.name }}</h2>
      <h6>{{ project.website }}</h6>
      <p>{{ project.desc }}</p>
      <div class="links">
        <a
          v-for="link in project.links"
          :href="link.href"
          v-bind:key="link.type"
          :target="link.href.startsWith('http') ? '_blank' : ''"
          ><i :class="`fa fa-${link.type}`"></i
        ></a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Project",
  props: ["project"],
};
</script>

<style scoped>
.project {
  display: table;
}

h2 {
  margin-bottom: 0;
}

h6 {
  margin: 0;
}

img {
  width: 100%;
  height: 100%;
}

.links a {
  bottom: 0;
  right: 0;
  color: var(--color);
  font-size: 2em;
  padding: 0.25em;
}
</style>
