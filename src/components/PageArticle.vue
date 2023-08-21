<template>
  <div class="article">
    <div class="article__img" v-if="article.image">
      <img :src="article.image" alt="" />
    </div>
    <div class="article__info">
      <div class="article__date">
        <span>{{ timeFormating().day }}</span>
        <div class="article__wrap">
          <div>{{ timeFormating().month }}</div>
          <div>{{ timeFormating().year }}</div>
        </div>
      </div>
      <h2 class="article__name">{{ article.name }}</h2>
      <p class="article__text">{{ article.previewText }}</p>
    </div>

    <div class="article__tag">{{ article.type.value }}</div>
  </div>
</template>

<script>
export default {
  name: "PageArticle",
  props: {
    article: {
      type: Object,
      default: () => {},
    },
  },
  methods: {
    timeFormating() {
      const monthList = [
        "January",
        "February",
        "March",
        "April",
        "May",
        "June",
        "July",
        "August",
        "September",
        "October",
        "November",
        "December",
      ];
      const dateFormat = new Date(this.article.date * 1000);
      const day = dateFormat.getDate();
      const month = monthList[dateFormat.getMonth()];
      const year = dateFormat.getFullYear();
      return { day, month, year };
    },
  },
};
</script>

<style>
.article {
  position: relative;
  border: 1px solid #0f62fe;
  border-radius: 16px;
  min-height: 658px;
  padding-bottom: 67px;
}

.article__info {
  padding: 32px;
  min-height: 304px;
}

.article__date {
  color: #a1a7b5;
  font-size: 36px;
  display: flex;
  align-items: center;
  font-weight: 700;
  margin-bottom: 9px;
}

.article__wrap {
  font-size: 15px;
}

.article__name {
  font-weight: 400;
  font-size: 22px;
  line-height: 26px;
  color: #0c5bef;
  margin: 0 0 45px;
}

.article__img {
  width: 100%;
  height: 250px;
}

.article__text {
  font-size: 20px;
  font-weight: 400;
  line-height: 26px;
  letter-spacing: -1.9px;
  color: #222327;
  margin: 0 0 20px;
}

.article__img img {
  width: 100%;
  height: 100%;
  border-top-left-radius: 16px;
  border-top-right-radius: 16px;
}

.article__tag {
  position: absolute;
  bottom: 36px;
  background-color: #f0f6fe;
  padding: 0 16px;
  border-radius: 16px;
  color: #00133a;
  font-size: 14px;
  line-height: 28px;
  height: 28px;
  margin-top: auto;
  margin-left: 32px;
}
</style>
