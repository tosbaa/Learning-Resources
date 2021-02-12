<template>
  <the-header title="Remember Me"></the-header>
  <stored-resources :resources="storedResources"></stored-resources>
</template>

<script>
import StoredResources from "./components/learning-resource/StoredResources";
import TheHeader from "./components/layouts/TheHeader.vue";
export default {
  components: { StoredResources, TheHeader },
  data() {
    return {
      storedResources: [
        {
          id: "official-guide",
          title: "Official Guide",
          description: "The official Vue.js documentation.",
          link: "https://vuejs.org",
        },
        {
          id: "google",
          title: "Google",
          description: "Most popular search engine",
          link: "https://www.google.com",
        },
      ],
    };
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@100;400;700&display=swap");
*,
*::after,
*::before {
  box-sizing: border-box;
}
html {
  font-family: "Roboto", sans-serif;
}

body {
  margin: 0;
}
</style>