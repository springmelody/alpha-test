<template>
  <header class="header">
    <page-logo logoSize="43" textSize="40"></page-logo>
  </header>
</template>

<script>
import PageLogo from "@/components/PageLogo.vue";
export default {
  name: "PageHeader",
  components: {
    PageLogo,
  },
};
</script>

<style scoped>
.header {
  background-color: #ffffff;
  padding: 49px 100px 38px;
}
</style>
