<script>
import ProjectCard from "./ProjectCard.vue";

export default {
    props: {
        projects: Array,
        title: String,
    },

    components: {
        ProjectCard,
    }
}
</script>

<template>
    <section class="container">
        <h1 class="mb-4">{{ title }}</h1>
        <div v-if="projects.length" class="row g-4">
            <ProjectCard v-for="project in projects" :key="project.id" :project="project" class="col-md-4 d-flex">
            </ProjectCard>
        </div>
        <h2 v-else class="text-muted">Non ci sono progetti.</h2>
    </section>
</template>

<style lang="scss" scoped></style>