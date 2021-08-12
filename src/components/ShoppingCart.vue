<template>
  <div class="purchases-container">
    <p className="article-quantity">ARTICLES (4)</p>
    <div :article="article" :key="article.id" v-for="article in articles" class="article-container">
      <img :src="article.image" :alt="article.title" />
      <div class="article-text-container">
        <p>{{article.title}}</p>
        <p>{{article.price}}</p>
        <p class="font-light">{{article.details[0].toLowerCase()}}</p>
        <p class="font-light">{{article.details[1]}}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ShoppingCart',
  props: {
    articles: Array,
  },
}
</script>

<style scope>
.purchases-container{
  position: relative;
  float: right;
  width: 30vw;
  margin-top: 5rem;
  color: var(--tedicolor);
}
.article-container{
  display: flex;
  height: 8rem;
  margin: 1rem;
  padding: .5rem;
  box-shadow: 2.5px 2.5px 5px 5px var(--verylightgrey);
}
.article-container img{
  margin: .5rem;
}
.article-text-container{
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: flex-start;
}
.article-text-container p{
  margin: 0;
}
.article-text-container p:first-child{
  font-size: 1.4rem;
  margin: .3rem 0;
}
.article-text-container p:nth-child(2){
  font-size: 1.3rem;
  margin: .5rem 0;
  margin-bottom: 1rem;
}
.article-quantity{
  margin-bottom: 0;
  margin-left: 1rem;
  font-size: 1.2rem;
  font-weight: lighter;
}
.font-light{
  font-weight: lighter;
}

</style>
