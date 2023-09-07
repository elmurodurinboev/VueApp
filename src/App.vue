<template>
  <the-header title="Remember Me"></the-header>
  <StoredResource :resources="storedResources"></StoredResource>
</template>
<script>
import TheHeader from './components/layout/TheHeader.vue';
import StoredResource from './components/learning-resources/StoredResource.vue';
export default {
  components: {
    StoredResource,
    TheHeader,
  },
  data() {
    return {
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
};
</script>
<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
  box-sizing: border-box;
}

html {
  font-family: 'Roboto', sans-serif;
}

body {
  margin: 0;
}
</style>
