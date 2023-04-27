<script>
export default {

    name: "ProjectCard",

    props: {
        project: Object,
        isDetail: Boolean,
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
                <h6>{{ isDetail ? project.description : abstract }}</h6>
            </div>
            <div class="card-footer d-flex justify-content-between">
                Created at: {{ project.created_at }}
                <router-link v-if="!isDetail" class="btn btn-primary btn-sm" :to="{
                        name: 'project-detail',
                        params: {
                            'id': project.id,
                        }
                    }">Vedi</router-link>
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped></style>