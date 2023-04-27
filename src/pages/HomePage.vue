<script>
import ProjectList from "../components/ProjectList.vue";

export default {
    components: {
        ProjectList
    },
}
</script>

<template>
    <ProjectList title="Più recenti" class="my-3" @changePage="fetchProjects">
    </ProjectList>
</template>

<style lang="scss" scoped></style>