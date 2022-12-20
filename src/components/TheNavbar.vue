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
      <div id="theme_group_options" @click="darkModeClass()">
        <TheIcon :icon="theme" />
      </div>
      <div id="navigation">
        <router-link to="/">Home</router-link>
        <router-link to="/works">Works</router-link>
        <router-link to="/skills">Skills</router-link>
        <router-link to="/about">About</router-link>
      </div>
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
      darkMode: false,
      theme: "",
    };
  },
  created() {
    window.addEventListener("resize", this.checkScreen);
    this.checkScreen();
    localStorage.getItem("theme") !== null
      ? (this.theme = localStorage.getItem("theme"))
      : (this.theme = "light_mode");
  },
  watch: {
    darkMode() {
      this.theme = this.darkMode ? "dark_mode" : "light_mode";
      localStorage.setItem("theme", this.theme);
    },
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
    darkModeClass() {
      this.darkMode = !this.darkMode;
      localStorage.setItem("theme", this.theme);
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
    width: 40%;
    padding: 4px;
    display: flex;
    justify-content: space-between;
    align-items: center;

    #theme_group_options {
      @include reset();
      @include positionCenter();
      cursor: pointer;
    }

    #navigation {
      width: 80%;
      height: 100%;
      display: flex;
      justify-content: space-between;
      align-items: center;

      a {
        font-weight: $font-weight-medium;
        color: $color-primary-dark;
        text-decoration: none;

        &:hover {
          color: $color-gray;
        }

        &.router-link-exact-active {
          color: $color-green;
          font-weight: $font-weight-xbold;
          text-decoration: dashed underline;

          &:hover {
            color: $color-gray;
          }
        }
      }
    }
  }
}
</style>
