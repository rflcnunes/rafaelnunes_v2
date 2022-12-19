<template>
  <div>
    <span class="material-icons">{{ icon }}</span>
  </div>
</template>

<script>
export default {
  name: "TheIcon",
  props: {
    icon: {
      type: String,
      required: true,
    },
  },
};
</script>

<style lang="scss" scoped>
//
</style>
