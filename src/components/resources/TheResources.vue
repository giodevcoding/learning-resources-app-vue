<script lang="ts">
import StoredResources from "./StoredResources.vue";
import AddResource from "./AddResource.vue";

export default {
    components: {
        StoredResources,
        AddResource,
    },

    provide() {
        return {
            resources: this.storedResources,
            addResource: this.addResource,
            removeResource: this.removeResource,
        };
    },

    data() {
        return {
            selectedTab: "StoredResources",
            storedResources: [
                {
                    id: "official-guide",
                    title: "Official Guide",
                    description: "The official Vue.js documentation.",
                    link: "https://vuejs.org",
                },
                {
                    id: "google",
                    title: "Google",
                    description: "Learn to google",
                    link: "https://google.com",
                },
            ],
        };
    },

    computed: {
        buttonModeStoredResources() {
            return this.selectedTab === "StoredResources" ? null : "flat";
        },

        buttonModeAddResource() {
            return this.selectedTab === "AddResource" ? null : "flat";
        },
    },

    methods: {
        setSelectedTab(tab: string) {
            this.selectedTab = tab;
        },
        addResource(title: string, description: string, link: string) {
            const newResource = {
                id: new Date().toISOString(),
                title,
                description,
                link,
            };

            this.storedResources.unshift(newResource);
            this.selectedTab = "StoredResources";
        },
        removeResource(resID: string) {
            const resIndex = this.storedResources.findIndex(res => res.id === resID);
            this.storedResources.splice(resIndex, 1);
        }
    },
};
</script>

<template>
    <BaseCard class="the-resources__button-container">
        <BaseButton
            class="the-resources__button"
            @click="setSelectedTab('StoredResources')"
            :mode="buttonModeStoredResources"
        >
            Stored Resources
        </BaseButton>
        <BaseButton
            class="the-resources__button"
            @click="setSelectedTab('AddResource')"
            :mode="buttonModeAddResource"
        >
            Add Resource
        </BaseButton>
    </BaseCard>
    <KeepAlive>
        <component :is="selectedTab"></component>
    </KeepAlive>
</template>

<style lang="scss" scoped>
.the-resources {
    &__button-container {
        display: flex;

        justify-content: space-evenly;
        align-items: center;
    }

    &__button {
        width: 40%;

        font-weight: bold;

        border-radius: 1rem;
    }
}
</style>
