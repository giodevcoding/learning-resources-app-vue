<script lang="ts">
export default {
    props: {
        title: {
            type: String,
            required: false,
        },
    },
    emits: ["close"],
};
</script>

<template>
    <teleport to="body">
        <div class="base-dialog-background" @click="$emit('close')"></div>
        <dialog class="base-dialog" open>
            <header class="base-dialog__header">
                <slot name="header">
                    <h2 class="base-dialog__heading">{{ title }}</h2>
                </slot>
            </header>
            <section class="base-dialog__details">
                <slot></slot>
            </section>
            <menu class="base-dialog__buttons">
                <slot name="actions">
                    <BaseButton @click="$emit('close')">Close</BaseButton>
                </slot>
            </menu>
        </dialog>
    </teleport>
</template>

<style lang="scss" scoped>
.base-dialog-background {
    width: 100%;
    height: 100vh;

    position: fixed;
    top: 0;
    left: 0;
    z-index: 10;

    background-color: rgba(0, 0, 0, 0.75);
}

.base-dialog {
    width: 80%;

    position: fixed;
    top: 20vh;
    left: 10%;
    z-index: 100;

    border: none;
    border-radius: 1.2rem;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
    overflow: hidden;

    @media (min-width: 768px) {
        & {
            width: 65rem;

            left: calc(50% - 32.5rem);
        }
    }

    &__header {
        width: 100%;
        padding: 2rem;

        color: white;

        background-color: var(--color-secondary);
    }

    &__details {
        padding: 2rem;
    }

    &__buttons {
        display: flex;
        padding: 2rem;

        justify-content: flex-end;
    }
}
</style>
