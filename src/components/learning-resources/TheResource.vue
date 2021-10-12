

<template>
  <base-card>
    <base-button @click="setSelectedTab('stored-resource')" :mode="getModeOn1"
      >Stored Resources
    </base-button>
    <base-button @click="setSelectedTab('add-resource')" :mode="getModeOn2"
      >Add Resource
    </base-button>
  </base-card>
  <keep-alive>
    <component :is="selectedTab"></component>
  </keep-alive>
</template>


<script>
import BaseCard from "../UI/BaseCard.vue";
import StoredResource from "./StoredResource.vue";
import AddResource from "./AddResource.vue";

export default {
  components: { BaseCard, StoredResource, AddResource },
  data() {
    return {
      selectedTab: "stored-resource",
      storedResources: [
        {
          id: "yah",
          title: "yahoo",
          desc: "search engine",
          link: "https://in.search.yahoo.com/",
        },
        {
          id: "goog",
          title: "google",
          desc: "best search engine",
          link: "https://www.google.com/",
        },
      ],
    };
  },
  provide() {
    return {
      resources: this.storedResources,
      addResource: this.addResource,
    };
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
    addResource(title, desc, url) {
      const newResource = {
        id: new Date().toISOString(),
        title: title,
        desc: desc,
        link: url,
      };
      this.storedResources.unshift(newResource);
      this.selectedTab = "stored-resource";
    },
  },
  computed: {
    getModeOn1() {
      return this.selectedTab === "stored-resource" ? null : "flat";
    },
    getModeOn2() {
      return this.selectedTab === "add-resource" ? null : "flat";
    },
  },
};
</script>

<style scoped>
</style>