<template>
  <the-header title="Remember Me"></the-header>
  <the-resources></the-resources>
</template>

<script>
import TheHeader from "./components/layouts/TheHeader.vue";
import TheResources from "./components/learning-resource/TheResources"
export default {
  components: { TheResources, TheHeader },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;700&display=swap");
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