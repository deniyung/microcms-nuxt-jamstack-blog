<template>
  <h1>記事一覧</h1>
  <ul>
    <li v-for="content in contents" :key="content.id">
      <nuxt-link :to="`/${content.id}`">{{ content.title }}</nuxt-link>
    </li>
  </ul>
</template>

<script>
import axios from "axios";
export default {
  async asyncData() {
    const { data } = await axios.get(
      // your-service-id部分は自分のサービスidに置き換えてください
      "https://deni.microcms.io/api/v1/blog",
      {
        // your-api-key部分は自分のapi-keyに置き換えてください
        headers: { "X-API-KEY": "87ccf72c-a283-4116-883f-221575df1375" }
      }
    );
    return data;
  }
};
</script>

<style lang="scss" scoped>
.main {
  width: 960px;
  margin: 0 auto;
}

.title {
  margin-bottom: 20px;
}

.publishedAt {
  margin-bottom: 40px;
}

.post {
  & > h1 {
    font-size: 30px;
    font-weight: bold;
    margin: 40px 0 20px;
    background-color: #eee;
    padding: 10px 20px;
    border-radius: 5px;
  }

  & > h2 {
    font-size: 24px;
    font-weight: bold;
    margin: 40px 0 16px;
    border-bottom: 1px solid #ddd;
  }

  & > p {
    line-height: 1.8;
    letter-spacing: 0.2px;
  }

  & > ol {
    list-style-type: decimal;
    list-style-position: inside;
  }
}
</style>
