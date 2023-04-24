<script>
export default {

    name: "ProjectCard",

    props: {
        project: Object,
    },

    computed: {
        abstract() {
            return this.project.description.slice(0, 50) + "...";
        }
    }
}
</script>

<template>
    <div>
        <div class="card">
            <div class="card-header">
                <h3>{{ project.name }}</h3>
            </div>
            <div class="card-body">
                <h6>{{ abstract }}</h6>
            </div>
            <div class="card-footer">
                Created at: {{ project.created_at }}
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped></style>