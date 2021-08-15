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
    // les variables qui vont stocker les résultats d'appelles des apis fictifs
    return{
      navElems: [],
      articles: [],
      infoShopping: [],
      deliveryStatus: [],
      deliverySection: [],
    // le Api fictif qui contient 5 tableaux d'objets pour remplir de différentes section avec les info et images
      api: 'https://my-json-server.typicode.com/OlgaSpirkina/Tedi/',
    }
  },
  // appelles sous la forme de await Promise.all vers apis fictifs crées avec my-json-server
  async created(){
    await Promise.all([
      fetch(this.api + 'navbar'),
      fetch(this.api + 'purchases'),
      fetch(this.api + 'info'),
      fetch(this.api + 'delivery'),
      fetch(this.api + 'deliverySection')
    ]).then((values) => {
      Promise.all([
        values[0].json(),
        values[1].json(),
        values[2].json(),
        values[3].json(),
        values[4].json(),
      ]).then((values => {
        this.navElems = values[0],
        this.articles = values[1],
        this.infoShopping =  values[2],
        this.deliveryStatus = values[3],
        this.deliverySection = values[4]
      }))
      .catch((err) => {
        console.log("There is an ERROR: " + err);
        return err;
      })
    })
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
  width: 80%;
  margin: 0 auto;
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
