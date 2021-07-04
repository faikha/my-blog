<template>
  <Layout>
    <div class="container">
      <h1>List articles</h1>
      <div v-for="article in $page.articles.edges" :key="article.id" class="article f-flex">
        <div class="article-img" :style="{'background-image': 'url('+ article.node.image + ')' }"></div>
        <div class="article-body">
          <g-link :to="article.node.path" class="article-link"></g-link>
          <h1 class="article-title">{{article.node.title}}</h1>
          <p class="article-abstract">{{article.node.abstract}}</p>
        </div>
      </div>
    </div>
  </Layout>
</template>

<page-query>
query{
  articles: allArticles{
    edges {
      node{
        id
        title
        abstract
        image
        path
      }
    }
  }
}
</page-query>

<script>
export default {
  metaInfo: {
    title: "My blog"
  }
};
</script>

<style>
.article {
  display: flex;
  align-items: center;
  box-shadow: 5px 5px 11px rgba(0, 0, 0, 0.15);
  border-radius: 8px;
  position: relative;
  margin-top: 50px;
  background-color: #fff;
}
@media screen and (max-width: 992px) {
  .article {
    display: block;
  }
}
.article-title {
  margin-top: 0;
}
.article-body {
  padding: 15px 30px;
}
.article-link {
  position: absolute;
  top: 0;
  right: 0;
  left: 0; 
  bottom: 0;
}
.article-img {
  width: 250px;
  height: 140px; 
  background-size: cover;
  background-position: center;
  border-radius: 8px;
  margin-right: 15px;
}@media screen and (max-width: 992px) {
  .article__img {
    width: 100%;
    height: 180px;
  }
}
</style>