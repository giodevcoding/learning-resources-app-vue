<script lang="ts">
import { inject } from "vue";

export default {
    setup() {
        return {
            addResource: inject("addResource") as Function,
        };
    },
    data() {
        return {
            inputIsInvalid: false,
        };
    },
    methods: {
        submitData() {
            const enteredTitle = (this.$refs.titleInput as HTMLInputElement)
                .value;
            const enteredDesc = (this.$refs.descInput as HTMLTextAreaElement)
                .value;
            const enteredLink = (this.$refs.linkInput as HTMLInputElement)
                .value;

            if (
                enteredTitle.trim() === "" ||
                enteredDesc.trim() === "" ||
                enteredLink.trim() === ""
            ) {
                this.inputIsInvalid = true;
                return;
            }

            this.addResource(enteredTitle, enteredDesc, enteredLink);
        },
        
        confirmError() {
            this.inputIsInvalid = false;
        }
    },
};
</script>

<template>
    <BaseDialog v-if="inputIsInvalid" title="Invalid Input" @close="confirmError">
        <template #default>
            <p>Unfortunately, at least one input value is invalid.</p>
            <p>Please check all inputs and make sure that you enter at least a few characters into each input field.</p>
        </template>
        <template #actions>
            <BaseButton @click="confirmError">Okay</BaseButton>
        </template>
    </BaseDialog>
    <div class="add-resource">
        <BaseCard>
            <form @submit.prevent="submitData">
                <div class="add-resource__form-field">
                    <label class="add-resource__input-label" for="title">
                        Title
                    </label>
                    <input
                        id="title"
                        class="add-resource__input"
                        name="title"
                        type="text"
                        ref="titleInput"
                    />
                </div>
                <div class="add-resource__form-field">
                    <label class="add-resource__input-label" for="description">
                        Description
                    </label>
                    <textarea
                        id="description"
                        class="add-resource__input"
                        name="description"
                        rows="3"
                        ref="descInput"
                    ></textarea>
                </div>
                <div class="add-resource__form-field">
                    <label class="add-resource__input-label" for="link">
                        Link
                    </label>
                    <input
                        id="link"
                        class="add-resource__input"
                        name="link"
                        type="url"
                        ref="linkInput"
                    />
                </div>
                <div>
                    <BaseButton type="submit">Add Resource</BaseButton>
                </div>
            </form>
        </BaseCard>
    </div>
</template>

<style lang="scss" scoped>
.add-resource {
    &__form-field {
        margin: 2rem 0;
    }

    &__input-label {
        display: block;
        margin-bottom: 1rem;

        font-weight: bold;
    }

    &__input {
        display: block;
        width: 100%;
        padding: 0.5rem;

        font: inherit;

        border: 1px solid #ccc;

        &:focus {
            background-color: #f7ebff;
            border-color: var(--color-secondary);
            outline: none;
        }
    }
}
</style>
