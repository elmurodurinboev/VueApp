<template>
  <base-card>
    <base-button
      @click="setResourceTab('stored-resources')"
      :mode="setResButtoon"
      >Stored Resources</base-button
    >
    <base-button @click="setResourceTab('add-resource')" :mode="setAdResButtoon"
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
          title: 'The official guide',
          description: 'More information in the website.',
          link: 'https//:vue.org',
        },
        {
          id: 'gooogle',
          title: 'The Google',
          description: 'To know more information',
          link: 'https//:google.org',
        },
      ],
    };
  },

  computed: {
    setResButtoon() {
      return this.selectedTab === 'stored-resources' ? null : 'flat';
    },
    setAdResButtoon() {
      return this.selectedTab === 'add-resource' ? null : 'flat';
    },
  },

  methods: {
    setResourceTab(tab) {
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
      this.selectedTab = 'stored-resources';
    },
  },
  provide() {
    return {
      resources: this.storedResources,
      addResource: this.addResource,
    };
  },
};
</script>
<style></style>
