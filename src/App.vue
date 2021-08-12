<template>
  <Navbar
    :navElems="navElems"
    :imagePathText="require('./assets/logo-text.png')"
    :imagePathShoppingCart="require('./assets/shoppingcart.png')"
   />
   <p></p>
   <div class="container-horizontal">
    <ShoppingCart
     :articles="articles"
    />
   </div>

</template>

<script>
import Navbar from './components/Navbar.vue'
import ShoppingCart from './components/ShoppingCart.vue'
export default {
  name: 'App',
  components: {
    Navbar,
    ShoppingCart,
  },
  data(){
    return{
      navElems: [],
      articles: [],
    }
  },
  methods: {
    async addNavItems(){
      const res = await fetch('http://localhost:5000/navbar')
      const data = await res.json()
      return data
    },
    async addShoppingCart(){
      const res = await fetch('http://localhost:5000/purchases')
      const data = await res.json()
      return data
    },
  },

  async created(){
    this.navElems = await this.addNavItems()
    this.articles = await this.addShoppingCart()
  },
}
</script>

<style>
@font-face {
  font-family: 'Gill Sans Std Light';
  src: local('Gill Sans Std Light'), url(./fonts/GillSansStd-Light.otf) format('truetype');
}
:root{
  --tedicolor:  #202446;
  --lightgrey: #d7d7d7;
  --verylightgrey: #ebebeb;
  --tedifont: 'Gill Sans Std Light', Helvetica Neue;
  --fonttext: "Alice", serif;
}
body{
  margin: 0;
  padding: 0;
  font-family: var(--tedifont);
}
.container-horizontal{
  width: 100%;
  display: flex;
  justify-content: space-around;
  align-items: center;
}
.container-vertical{
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
}
.box{
  border-bottom: 1px solid var(--lightgrey);
  box-shadow: 1px 2.5px 2px 2.5px var(--verylightgrey);
  background-color: #fff;
  margin-bottom: 10rem;
}

</style>
