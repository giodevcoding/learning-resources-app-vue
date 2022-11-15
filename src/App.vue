<script lang="ts">
import TheHeader from "./components/layouts/TheHeader.vue";
import TheResources from "./components/resources/TheResources.vue";

export default {
    components: {
        TheHeader,
        TheResources,
    },
};
</script>

<template>
    <TheHeader title="RememberMe" />
    <TheResources />
</template>

<style lang="scss">
@import "./scss/abstracts/variables";

@import "./scss/base/base";
</style>
