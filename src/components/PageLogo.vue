<template>
  <div class="logo">
    <img :width="logoSize" :height="logoSize" src="../assets/logo.svg" alt="" />
    <a href="/" class="logo__link" :style="{ fontSize: textSize + 'px' }"
      >alpha</a
    >
  </div>
</template>

<script>
export default {
  name: "PageLogo",
  props: {
    logoSize: {
      type: String,
      default: "43",
    },
    textSize: {
      type: String,
      default: "40",
    },
  },
};
</script>

<style scoped>
.logo {
  display: flex;
  align-items: center;
}

.logo__link {
  text-decoration: none;
  color: #1d37af;
  font-weight: 900;
  padding-left: 8px;
}
</style>
