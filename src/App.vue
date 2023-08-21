<template>
  <page-header></page-header>
  <main class="main">
    <div class="top">
      <h1 class="title">Новости</h1>
    </div>
    <div class="container" v-if="this.articles.length">
      <div class="row">
        <div class="col" v-for="article in articles" :key="article.code">
          <page-article :article="article"></page-article>
        </div>
      </div>
      <button class="loadBtn" @click="fetchNews" v-if="isPageAvailable">
        Загрузить ещё
      </button>
    </div>
    <div class="container" v-else>
      <page-spinner></page-spinner>
    </div>
  </main>
  <page-footer></page-footer>
</template>

<script>
import PageHeader from "@/components/PageHeader.vue";
import PageFooter from "@/components/PageFooter.vue";
import PageArticle from "@/components/PageArticle.vue";
import PageSpinner from "@/components/PageSpinner.vue";

export default {
  name: "App",
  components: {
    PageHeader,
    PageFooter,
    PageArticle,
    PageSpinner,
  },
  data() {
    return {
      page: 1,
      articles: [],
      isPageAvailable: false,
    };
  },
  mounted() {
    this.fetchNews();
  },
  methods: {
    async fetchNews() {
      try {
        const f = await fetch(
          `https://flems.github.io/test/api/news/${this.page}`
        );
        this.isPageAvailable = true;
        const data = await f.json();
        this.articles = [...this.articles, ...data.items];
        this.page += 1;

        if (data.nav.current === data.nav.total) {
          this.isPageAvailable = false;
        }
      } catch (e) {
        alert("Load error");
      }
    },
  },
};
</script>

<style scoped>
.container {
  max-width: 1920px;
  margin: 0 auto;
  padding: 67px 100px 72px;
}

.row {
  display: flex;
  flex: 0 0 auto;
  flex-wrap: wrap;
  width: 100%;
  margin: 0 -24px;
}

.col {
  width: 33.33%;
  padding: 0 24px;
  margin-bottom: 64px;
}

.articles {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}

.top {
  display: flex;
  min-height: 320px;
  background-image: url(./assets/bg.jpg);
  background-size: cover;
  padding: 20px 100px;
}

.title {
  color: #17171a;
  font-size: 40px;
  font-weight: 700;
  line-height: 48px;
  letter-spacing: -1px;
  margin-top: auto;
}

.loadBtn {
  cursor: pointer;
  display: block;
  margin: 0 auto;
  color: #002dbf;
  background: none;
  font-size: 20px;
  line-height: 56px;
  height: 56px;
  padding: 0 32px;
  border-radius: 8px;
  border: 1px solid #002dbf;
}
</style>
