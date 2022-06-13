<template>
  <the-header :title="'RememberMe'"></the-header>
  <the-resources></the-resources>
  <!-- <stored-resource :resources="storedResources"></stored-resource> -->
</template>
<script>
import TheHeader from './components/layouts/TheHeader.vue';
import TheResources from './components/learning-resource/TheResources.vue';
// import LearningResource from './components/learning-resource/LearningResource.vue';
export default {
  components: {
    TheHeader,
    TheResources,
    // LearningResource,
  },
  data() {
    return {};
  },
};
</script>
<style>
* {
  box-sizing: border-box;
}
html {
  font-family: sans-serif;
}
body {
  margin: 0;
}
</style>
