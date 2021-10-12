<template>
  <the-header :title="title"></the-header>
  <!-- <stored-resource :stored-resources="storedResources"> </stored-resource> -->
  <the-resource> </the-resource>
</template>

<script>
import TheHeader from "./components/layouts/TheHeader.vue";
import TheResource from "./components/learning-resources/TheResource.vue";
// import StoredResource from "./components/learning-resources/StoredResource.vue";

export default {
  name: "App",
  components: {
    TheHeader,
    TheResource,
  },
  data() {
    return {
      title: "Resource App",
    };
  },
};
</script>



<style>
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap");

* {
  box-sizing: border-box;
}

html {
  font-family: "Roboto", sans-serif;
}

body {
  margin: 0;
}
</style>
