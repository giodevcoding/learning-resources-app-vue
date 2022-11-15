<script lang="ts">
import { inject } from "vue";
import LearningResource from "./LearningResource.vue";

export interface LearningResourceInterface {
    id: string;
    title: string;
    description: string;
    link: string;
}

export default {
    components: {
        LearningResource,
    },
    setup() {
        return {
            resources: inject("resources") as Array<LearningResourceInterface>,
        };
    },
};
</script>

<template>
    <ul class="stored-resources">
        <LearningResource
            v-for="resource in resources"
            :key="resource.id"
            :id="resource.id"
            :title="resource.title"
            :description="resource.description"
            :link="resource.link"
        />
    </ul>
</template>

<style lang="scss" scoped>
.stored-resources {
    max-width: 65rem;
    margin: 0 auto;

    list-style: none;
}
</style>
