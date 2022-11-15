<script lang="ts">
import { inject, type PropType } from 'vue';

export default {
    props: {
        id: {
            type: String
        },
        title: {
            type: String,
            required: true,
        },
        description: {
            type: String,
            default: "",
        },
        link: {
            type: String,
            default: "#",
        },
    },
    setup() {
        return {
            removeResource: inject('removeResource') as Function
        }
    },
    methods: {
    },
};
</script>

<template>
    <li class="learning-resource">
        <BaseCard>
            <header class="learning-resource__header">
                <h3 class="learning-resource__title">{{ title }}</h3>
                <BaseButton class="learning-resource__delete" mode="flat" @click="removeResource(id)">Delete</BaseButton>
            </header>
            <p class="learning-resource__description">{{ description }}</p>
            <nav class="learning-resource__nav">
                <a class="learning-resource__link" :href="link"
                    >View Resource
                </a>
            </nav>
        </BaseCard>
    </li>
</template>

<style lang="scss" scoped>
.learning-resource {
    max-width: 65rem;
    margin: 0 auto;

    &__header {
        display: flex;
        margin: .6rem 0 1.2rem;

        justify-content: space-between;
        align-items: center;

        //list-style: none;
    }

    &__title {
        font-size: 2.4rem;
    }

    &__delete {
    }

    &__description {
    }

    &__nav {
        margin: 0.5rem 0;
    }

    &__link,
    &__link:link {
        color: var(--color-tertiary);
        text-decoration: none;

        transition: color 0.1s;

        &:hover,
        &:active {
            color: var(--color-tertiary-light);
        }
    }
}
</style>
