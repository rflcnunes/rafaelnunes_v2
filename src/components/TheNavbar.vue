<template>
  <nav>
    <img
      v-if="!mobile"
      id="icon"
      src="@/assets/robot_icon.svg"
      alt="robot_icon"
    />
    <TheIcon v-else icon="menu" />
    <i class="bi bi-list"></i>
    <div id="options">
      <router-link to="/">Home</router-link>
      <router-link to="/works">Works</router-link>
      <router-link to="/skills">Skills</router-link>
      <router-link to="/about">About</router-link>
    </div>
  </nav>
</template>

<script>
const TheIcon = () => import("@/components/TheIcon.vue");
export default {
  name: "TheNavbar",
  components: {
    TheIcon,
  },
  data() {
    return {
      screen: window.innerWidth,
      mobile: false,
      mobileNav: false,
    };
  },
  created() {
    window.addEventListener("resize", this.checkScreen);
    this.checkScreen();
  },
  methods: {
    checkScreen() {
      this.windowWidth = window.innerWidth;

      if (this.windowWidth <= 568) {
        this.mobile = true;
        return;
      }

      this.mobile = false;
      this.mobileNav = false;
    },
  },
};
</script>

<style lang="scss" scoped>
@import "@/style/scss/_variables.scss";

@media screen and (max-width: 568px) {
  nav {
    flex-direction: column;
    align-items: center;

    #icon {
      margin-bottom: 20px;
    }

    #options {
      width: 100%;
      justify-content: center;
      flex-wrap: wrap;

      a {
        margin: 10px;
      }
    }
  }
}

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
