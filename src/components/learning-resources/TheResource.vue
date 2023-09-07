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
  <component :is="resourcesTab"></component>
</template>
<script>
import StoredResources from './StoredResources.vue';
import AddResource from './AddResource.vue';
export default {
  components: { StoredResources, AddResource },
  data() {
    return {
      resourcesTab: 'stored-resources',
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
      return this.resourcesTab === 'stored-resources' ? null : 'flat';
    },
    setAdResButtoon() {
      return this.resourcesTab === 'add-resource' ? null : 'flat';
    },
  },
  provide() {
    return {
      resources: this.storedResources,
    };
  },
  methods: {
    setResourceTab(tab) {
      this.resourcesTab = tab;
    },
  },
};
</script>
<style></style>
