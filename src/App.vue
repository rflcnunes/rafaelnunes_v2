<template>
  <div id="app">
    <TheNavbar />
    <router-view />
  </div>
</template>

<script>
const TheNavbar = () => import("@/components/TheNavbar.vue");

export default {
  name: "App",
  components: {
    TheNavbar,
  },
};
</script>

<style lang="scss">
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
