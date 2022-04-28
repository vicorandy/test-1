<template>
  <the-header title="RememberME"></the-header>
  <the-resoucres></the-resoucres>
</template>

<script>
import TheHeader from './components/Layouts/TheHeader.vue';
import TheResoucres from './components/resources/TheResources.vue';

export default {
  components: { TheHeader, TheResoucres },
};
</script>
<style>
@import url('https://fonts.googleleapis.com/css@?family=roboto:wght@');
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
