<template>
  <form>
    <h3>Add New project</h3>

    <p class="twoInputs">
      <label for="">
        Project Title
        <br />
        <input v-model="title" type="text" />
      </label>
      <label for="">
        Image URL
        <br />
        <input v-model="image" type="url" />
      </label>
    </p>

    <p class="projectDescription">
      <label for="">
        Project Description
        <br />
        <textarea v-model="description" cols="30" rows="10"></textarea>
      </label>
    </p>
    
    <button @click.prevent="handleSubmit">SUBMIT</button>
  </form>
</template>

<script>
export default {
  name: "AdminView",
  data() {
    return {
      title: '',
      image: '',
      description: '',
    };
  },
  methods: {
    handleSubmit() {
      this.$emit("createProject", {
        title: this.title,
        image: this.image,
        description: this.description,
      })
      this.reset();
    },
    reset() {
      this.title = "";
      this.image = "";
      this.description = "";
    }
  },
};
</script>

<style></style>
