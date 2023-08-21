<template>
  <footer class="footer">
    <page-logo :logoSize="32" :textSize="30"></page-logo>
    <p class="copyright">© alpha, 2023</p>
  </footer>
</template>

<script>
import PageLogo from "@/components/PageLogo.vue";
export default {
  name: "PageFooter",
  components: {
    PageLogo,
  },
};
</script>

<style scoped>
.footer {
  background-color: #f0f6fe;
  padding: 62px 100px 44px;
}

.copyright {
  font-weight: 400;
  line-height: 22px;
  color: #81899d;
}
</style>
