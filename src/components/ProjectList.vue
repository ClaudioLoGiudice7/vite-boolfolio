<script>
import axios from "axios";
import ProjectCard from "./ProjectCard.vue";
import AppPagination from "./AppPagination.vue";

export default {
    data() {
        return {
            projects: {
                list: [],
                pages: [],
            },
        }
    },

    props: {
        title: String,
    },

    components: {
        ProjectCard, AppPagination,
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
}
</script>

<template>
    <section>
        <h1 class="my-4">{{ title }}</h1>
        <div v-if="projects.list.length" class="row g-4">
            <ProjectCard v-for="project in projects.list" :key="project.id" :project="project" :isDetail="false"
                class="col-md-4 d-flex">
            </ProjectCard>
        </div>
        <h2 v-else class="text-muted">
            Non ci sono progetti.
        </h2>

        <AppPagination :pages="projects.pages" @changePage="fetchProjects"></AppPagination>
    </section>
</template>

<style lang="scss" scoped></style>