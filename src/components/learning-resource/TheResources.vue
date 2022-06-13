<template>
  <base-card>
    <base-button
      @click="setSelectedTab('stored-resource')"
      :mode="storedResButtonMode"
      >Stored Resource</base-button
    >
    <base-button
      @click="setSelectedTab('add-resource')"
      :mode="AddResButtonMode"
      >Add Resource</base-button
    >
  </base-card>
  <keep-alive>
    <component :is="selectedTab"></component>
  </keep-alive>
</template>
<script>
import StoredResource from './StoredResource.vue';
import AddResource from './AddResource.vue';
export default {
  components: {
    StoredResource,
    AddResource,
  },
  computed: {
    storedResButtonMode() {
      return this.selectedTab === 'stored-resource' ? null : 'flat';
    },
    AddResButtonMode() {
      return this.selectedTab === 'add-resource' ? null : 'flat';
    },
  },
  provide() {
    return {
      resources: this.storedResources,
      addResource: this.addResource,
      deleteResource: this.removeResource,
    };
  },
  data() {
    return {
      selectedTab: 'stored-resource',
      storedResources: [
        {
          id: 'official-guide',
          title: 'Official Guide',
          description: 'The official Vue.js documentation',
          link: 'https://v3.cn.vuejs.org/',
        },
        {
          id: 'baidu',
          title: 'Baidu',
          description: 'Learn to Baidu...',
          link: 'https://www.baidu.com/',
        },
      ],
    };
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
    addResource(title, descripion, url) {
      const newResource = {
        id: new Date().toISOString(),
        title,
        descripion,
        link: url,
      };
      this.storedResources.unshift(newResource);
      this.selectedTab = 'stored-resource';
    },
    removeResource(resId) {
      // this.storedResources = this.storedResources.filter(
      //   (res) => res.id !== resId
      // );
      const resIndex = this.storedResources.findIndex(
        (res) => res.id === resId
      );
      this.storedResources.splice(resIndex, 1);
    },
  },
};
</script>
