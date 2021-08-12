<template>
  <div class="shopping-container">
    <div :article="article" :key="article.id" v-for="article in articles" >
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
.shopping-container{
  width: 40vw;
}
</style>
