<template>
    <div class="base-card">
        <slot></slot>
    </div>
</template>

<style lang="scss" scoped>
.base-card {
    max-width: 65rem;
    margin: 3rem auto;
    padding: 1.5rem 2.5rem;

    border-radius: 1.2rem;
    box-shadow: 0 2px .8rem rgba(0, 0, 0, .26);
}
</style>