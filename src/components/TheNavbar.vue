<template>
  <nav>
    <img id="icon" src="@/assets/robot_icon.svg" alt="robot_icon" />
    <div id="options">
      <router-link to="/">Home</router-link>
      <router-link to="/works">Works</router-link>
      <router-link to="/skills">Skills</router-link>
      <router-link to="/about">About</router-link>
    </div>
  </nav>
</template>

<script>
export default {
  name: "TheNavbar",
};
</script>

<style lang="scss" scoped>
@import "@/style/scss/_variables.scss";

nav {
  padding: 30px;
  font-family: $roboto-family;
  display: flex;
  justify-content: space-between;

  #icon {
    width: 50px;
    height: 50px;
    margin-right: 20px;
  }

  #options {
    width: 50%;
    padding: 4px;
    display: flex;
    justify-content: space-between;
    align-items: center;

    a {
      font-weight: $font-weight-medium;
      color: $color-primary-dark;
      text-decoration: none;

      &.router-link-exact-active {
        color: $color-green;
        font-weight: $font-weight-xbold;
        text-decoration: dashed underline;
      }
    }
  }
}
</style>
