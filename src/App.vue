<template>
  <Navbar
    :navElems="navElems"
    :imagePathText="require('./assets/logo-text.png')"
    :imagePathShoppingCart="require('./assets/shoppingcart.png')"
   />
   <Banner title="suivi de commande" />
   <div class="container-horizontal shopping">
     <Purchase
       :infoShopping="infoShopping"
       :deliveryStatus="deliveryStatus"
     />
    <ShoppingCart
      :articles="articles"
    />
   </div>
   <Banner title="informations sur la livraison" />
   <DeliverySection
    :deliverySection="deliverySection"
   />
   <Banner title="informations sur le paement" />
   <PaymentInfo
    :visaPath="require('./assets/logo-cb.jpg')"
    title="VISA"
   />
   <Banner title="total commande" />
   <Total
   />
   <Banner title="besoin d'aide ?" />
   <Help />
</template>

<script>
import Navbar from './components/Navbar.vue'
import ShoppingCart from './components/ShoppingCart.vue'
import Purchase from './components/Purchase.vue'
import Banner from './components/Banner.vue'
import DeliverySection from './components/DeliverySection.vue'
import PaymentInfo from './components/PaymentInfo.vue'
import Total from './components/Total.vue'
import Help from './components/Help.vue'

export default {
  name: 'App',
  components: {
    Navbar,
    ShoppingCart,
    Purchase,
    Banner,
    DeliverySection,
    PaymentInfo,
    Total,
    Help,
  },
  data(){
    return{
      navElems: [],
      articles: [],
      infoShopping: [],
      deliveryStatus: [],
      deliverySection: [],
      api: 'https://my-json-server.typicode.com/OlgaSpirkina/Tedi/',
    }
  },
  methods: {
    async addNavItems(){
      const res = await fetch(this.api + 'navbar')
      const data = await res.json()
      return data
    },
    async addShoppingCart(){
      const res = await fetch(this.api + 'purchases')
      const data = await res.json()
      return data
    },
    async addInfoShopping(){
      const res = await fetch(this.api + 'info')
      const data = await res.json()
      return data
    },
    async delivery(){
      const res = await fetch(this.api + 'delivery')
      const data = await res.json()
      return data
    },
    async deliverySectionFunc(){
      const res = await fetch(this.api + 'deliverySection')
      const data = await res.json()
      return data
    },
    // async totalPriceFunc(){
    //   TotalData.map()
    // },
    // async helpSectionFunc(){
    //   const res = await fetch('http://localhost:5000/help')
    //   const data = await res.json()
    //   return data
    // },
  },

  async created(){
    this.navElems = await this.addNavItems()
    this.articles = await this.addShoppingCart()
    this.infoShopping = await this.addInfoShopping()
    this.deliveryStatus = await this.delivery()
    this.deliverySection = await this.deliverySectionFunc()
    // this.totalPrice = await this.totalPriceFunc()
    // this.helpSection = await this.HelpSectionFunc()
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
  /* margin-bottom: 10rem; */
}
.shopping{
  margin-top: 3rem;
  height: 55vh;
  align-items: flex-start;
}
@media only screen and (max-width : 800px) {
  .container-horizontal{
    flex-direction: column;
    align-items: center;
    height: inherit;
  }
}
@media only screen and (min-width : 801px) {
  .container-horizontal{
    height: inherit;
  }
}

</style>
