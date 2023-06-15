<template>
  <div>
    <div class="navbar">
    <button @click="isAdmin = true" :class="{ 'active': isAdmin === true }">ADMIN</button>
    <button @click="isAdmin = false" :class="{ 'active': isAdmin === false}">USER</button>
  </div>
  <h1 class="title">My Portfolio</h1>
    <admin-view v-if="isAdmin" @createProject="addProject"/>
    <user-view :allProjects="allProjects" v-else />
  </div>
</template>

<script>
import AdminView from "./components/AdminView.vue";
import UserView from "./components/UserView.vue";

export default {
  name: "app",
  components: {
    userView: UserView,
    adminView: AdminView
  },
  data() {
    return {
      isAdmin: true,
      allProjects: [
        {
        title: 'Project1',
        image: 'https://picsum.photos/id/10/200',
        description: 'blabla',
      },
      {
        title: 'Project2',
        image: 'https://picsum.photos/id/11/200',
        description: 'blabla',
      },
      {
        title: 'Project3',
        image: 'https://picsum.photos/id/12/200',
        description: 'blabla',
      }
      ]
    };
  },
  methods: {
    addProject(project) {
      this.allProjects.push(project);
    }
  }
};
</script>

<style>
body {
  padding: 50px;
  background-color: #bcefd0;
  color: #fc6472;
  text-align: center;
  font-family:'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif
}

button {
  margin: 10px;
  border-radius: 20px;
  border: 0;
  padding: 10px;
  color: #bcefd0;
  background-color: #23c8b2;
}

input {
  margin-top: 10px;
  width: 100%;
}

textarea {
  margin-top: 10px;
  width: 100%;
}

.title {
  padding: 50px;
}

.active {
  color:#fc6472;
  background-color: #eccdb3;
}

.navbar {
  display: flex;
  flex-direction: row-reverse;
}

.twoInputs {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 100px;
  text-align: left;
}

.projectDescription {
  text-align: left;
}
</style>
