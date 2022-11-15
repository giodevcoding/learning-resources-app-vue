<script lang="ts">

export default {
    props: {
        mode: {
            type: String,
            default: "",
        },
    },
    computed: {
        currentMode() {
            if (this.mode && this.mode.length <= 0) {
                return "";
            }
            return "base-button--" + this.mode;
        }
    }
}
</script>

<template>
    <button class="base-button" :class="currentMode">
        <slot></slot>
    </button>
</template>

<style lang="scss" scoped>
.base-button {
    padding: 1rem 2rem;

    color: white;
    font-family: inherit;

    background-color: var(--color-secondary);
    border: 1px solid var(--color-secondary);
    
    cursor: pointer;
    transition: all .1s;
    
    &:hover,
    &:active {
        background-color: var(--color-secondary-dark);
        border-color: var(--color-secondary-dark);
    }
    
    &--flat {
        color: var(--color-secondary);

        background-color: transparent;
        border: none;
        
        &:hover,
        &:active {
            background-color: var(--color-secondary-light);
        }
    }
}
</style>