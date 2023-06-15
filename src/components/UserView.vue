<template>
  <div class="detail">
    <img :src="selectedProject.image" :alt="selectedProject.title" class="imgDetail">
    <div class="detailText">
      <p>{{ selectedProject.title }}</p>
      <p>{{ selectedProject.description }}</p>
    </div>
  </div>
  <div v-if="allProjects.length > 0" class="grid">
    <article
      v-for="project in allProjects"
      :key="project.title"
      :project="project"
    >
      <img :src="project.image" :alt="project.title" @click="handleClick(project)" />
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
  data() {
    return {
      selectedProject: this.allProjects[0],
    };
  },
  methods: {
    handleClick(project) {
      this.selectedProject = project;
    }
  }
};
</script>

<style>
.grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 16px;
}
@media only screen and (max-width: 860px) {
  .grid {
    grid-template-columns: repeat(2, 1fr);
  }
  .detail {
  flex-direction: column;
  align-items: center;
}
.detailText {
  align-items: center;
}
}
.imgDetail {
  width: 300px;
  height: 300px;
  border-radius: 50%;
}
.detail {
  display: flex;
  margin: 60px 0 40px;
}
.detailText {
  display: flex;
  flex-direction: column;
  padding: 0 50px 0 50px;
  text-align: left;
}
</style>
