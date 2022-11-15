<script lang="ts">
export default {
    props: {
        title: {
            type: String,
            required: true,
        },
    },
}
</script>

<template>
    <header class="the-header">
        <h1 class="the-header__title">{{ title }}</h1>
    </header>
</template>

<style lang="scss" scoped>
    .the-header {
        display: flex;
        width: 100%;
        height: 8rem;

        justify-content: center;
        align-items: center;

        background-color: var(--color-primary);

        &__title {
            color: white;
        }
    }
</style>