<template>
  <div class="home" :class="theme">
    {{ theme }}
  </div>
</template>

<script>
//

export default {
  name: "HomeView",
  data() {
    return {
      darkMode: false,
    };
  },
  components: {
    //
  },
  created() {
    this.darkMode = localStorage.getItem("theme") === "dark_mode";
  },
  updated() {
    this.darkMode = localStorage.getItem("theme") === "dark_mode";
  },
  computed: {
    theme() {
      return this.darkMode ? "home-dark" : "home-light";
    },
  },
};
</script>

<style scoped>
.home-dark {
  background-color: #1a1a1a;
  color: #fff;
}

.home-light {
  background-color: #fff;
  color: #000;
}
</style>
