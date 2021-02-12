<template>
  <base-card>
    <base-button @click="selecTab('stored-resources')"
      >Stored Resources</base-button
    >
    <base-button @click="selecTab('add-resources')">Add Resource</base-button>
    <component :is="selectedTab"></component>
  </base-card>
</template>

<script>
import StoredResources from "./StoredResources.vue"
import AddResource from "./AddResource.vue"
export default {
  components: {
    StoredResources, AddResource
  },
  
  data() {
    return {
      selectedTab: "stored-resources",
    };
  },
  methods: {
    selectTab(tab) {
      this.selectedTab = tab;
    },
  },
};
</script>