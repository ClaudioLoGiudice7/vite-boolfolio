<script>

// IMPORT DEL COMPONENTE
import axios from "axios";
import AppHeader from "./components/AppHeader.vue";

// DEFINIZIONE DEL COMPONENTE IN PAGINA
export default {
  data() {
    return {
      title: "Hello!",
      projects: [],
    }
  },

  components: {
    AppHeader
  },

  methods: {
    fetchProjects() {
      axios
        .get("http://127.0.0.1:8000/api/projects")
        .then((response) => {
          this.projects = response.data;
        })
    }
  },

  created() {
    this.fetchProjects();
  }
};
</script>

<template>
  <AppHeader></AppHeader>
  <h1>{{ title }}</h1>
  <ul>
    <li v-for="project in projects">{{ project.name }}</li>
  </ul>
</template>


<style lang="scss"></style>