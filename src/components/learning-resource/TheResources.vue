<template>
  <base-card>
    <base-button @click="selectTab('stored-resources')" :mode="storedButtonMode"
      >Stored Resources</base-button
    >
    <base-button @click="selectTab('add-resource')" :mode="addButtonMode"
      >Add Resource</base-button
    >
  </base-card>
  <base-card>
    <component :is="selectedTab"></component>
  </base-card>
</template>

<script>
import StoredResources from "./StoredResources.vue";
import AddResource from "./AddResource.vue";
export default {
  components: {
    StoredResources,
    AddResource,
  },

  data() {
    return {
      selectedTab: "stored-resources",
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
          description: "Most popular search engine",
          link: "https://www.google.com",
        },
      ],
    };
  },

  computed: {
    storedButtonMode() {
      return this.selectedTab === "stored-resources" ? null : "flat";
    },
    addButtonMode() {
      return this.selectedTab === "add-resource" ? null : "flat";
    },
  },
  methods: {
    selectTab(tab) {
      this.selectedTab = tab;
    },
  },
  provide() {
    return {
      resources: this.storedResources,
    };
  },
};
</script>