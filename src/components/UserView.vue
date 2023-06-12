<template>
  <div v-if="allProjects.length > 0" class="grid">
    <article
      v-for="project in allProjects"
      :key="project.title"
      :project="project"
    >
      <img :src="project.image" :alt="project.title" />
      <div>
        <h2>{{ project.title }}</h2>
        <!-- <p>{{ project.description }}</p> -->
      </div>
    </article>
  </div>

  <div v-else>
    <p>No projects yet!</p>
    <p>Add a project to get started</p>
  </div>
</template>

<script>
export default {
  name: "UserView",
  props: ["allProjects"],
};
</script>

<style>
.grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 16px;
}
</style>
