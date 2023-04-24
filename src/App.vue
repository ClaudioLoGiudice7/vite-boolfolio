<script>

// IMPORT DEL COMPONENTE
import axios from "axios";
import AppHeader from "./components/AppHeader.vue";
import ProjectList from "./components/ProjectList.vue";

// DEFINIZIONE DEL COMPONENTE IN PAGINA
export default {
  data() {
    return {
      title: "Vue Portfolio",
      projects: [],
    }
  },

  components: {
    AppHeader, ProjectList,
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
  <AppHeader :title="title"></AppHeader>
  <ProjectList :projects="projects" title="Più recenti" class="my-3"></ProjectList>
</template>


<style lang="scss"></style>