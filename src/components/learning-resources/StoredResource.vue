<template>
  <ul>
    <learning-resource
      v-for="resource in resources"
      :key="resource.id"
      :title="resource.title"
      :desc="resource.desc"
      :link="resource.link"
    >
    </learning-resource>
  </ul>
</template>

<script>
import LearningResource from "./LearningResource.vue";
export default {
  name: "StoredResource",
  components: { LearningResource },
  inject: ["resources"],
};
</script>


<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}
</style>