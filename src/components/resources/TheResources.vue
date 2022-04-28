<template>
  <base-card>
    <base-button
      @click="setSelectedTab('stored-resources')"
      :mode="storedResButtonMode"
      >Stored Resources</base-button
    >
    <base-button
      @click="setSelectedTab('add-resource')"
      :mode="addResButtonMode"
      >Add Resource</base-button
    >
  </base-card>
  <keep-alive>
    <component :is="selectedTab"></component>
  </keep-alive>
</template>
<script>
import StoredResources from './StoredResources.vue';
import AddResource from './AddResource.vue';
export default {
  components: { StoredResources, AddResource },
  data() {
    return {
      selectedTab: 'stored-resources',
      storedResources: [
        {
          id: 'official-guide',
          title: 'Official Guide',
          description: 'the official Vue.js documentation.',
          link: 'https://vuejs.org',
        },
        {
          id: 'google',
          title: 'Google',
          description: 'learn to Google',
          link: 'https://google.com',
        },
      ],
    };
  },
  provide() {
    return {
      resources: this.storedResources,
      update: this.updateResource,
      deleteResource: this.removeResoucres,
    };
  },
  computed: {
    storedResButtonMode() {
      return this.selectedTab === 'stored-resources' ? null : 'flat';
    },
    addResButtonMode() {
      return this.selectedTab === 'add-resource' ? null : 'flat';
    },
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
    updateResource(newResource) {
      this.storedResources.unshift(newResource);
      this.selectedTab = 'stored-resources';
    },
    removeResoucres(resid) {
      const resIndex = this.storedResources.findIndex(
        (res) => res.id === resid
      );
      this.storedResources.splice(resIndex, 1);
    },
  },
};
</script>
