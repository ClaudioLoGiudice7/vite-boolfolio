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
      projects: {
        list: [],
        pages: [],
      },
    }
  },

  components: {
    AppHeader, ProjectList,
  },

  emits: ["changePage"],

  methods: {
    fetchProjects(endpoint = null) {

      if (!endpoint) endpoint = "http://127.0.0.1:8000/api/projects";

      axios
        .get(endpoint)
        .then((response) => {
          this.projects.list = response.data.data;
          this.projects.pages = response.data.links;
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
  <ProjectList :projects="projects.list" :pages="projects.pages" title="Più recenti" class="my-3"
    @changePage="fetchProjects"></ProjectList>
</template>

<style lang="scss"></style>