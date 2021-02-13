<template>
  <base-card>
    <base-button @click="selectTab('stored-resources')" :mode="storedButtonMode"
      >Stored Resources</base-button
    >
    <base-button @click="selectTab('add-resource')" :mode="addButtonMode"
      >Add Resource</base-button
    >
  </base-card>
    <keep-alive>
      <component :is="selectedTab"></component>
    </keep-alive>
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
    addResource(title, description, url) {
      const newResource = {
        id: new Date().toISOString(),
        title: title,
        description: description,
        link: url,
      };
      this.storedResources.unshift(newResource);
      this.selectedTab = "stored-resources";
    },

    removeResource(resId) {
      const resIndex = this.storedResources.findIndex(
        (res) => res.id === resId
      );
      this.storedResources.splice(resIndex, 1);
    },
  },
  provide() {
    return {
      resources: this.storedResources,
      addResource: this.addResource,
      removeResource: this.removeResource,
    };
  },
};
</script>