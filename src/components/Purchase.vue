<template>
  <!-- La section avec les info: N° commande, date d'expédition et livraison -->
  <div class="purchase-parent">
    <div
      :info="info"
      :key="info.id"
      class="purchase-info"
      v-for="info in infoShopping" >
      <p>{{info.name}}</p>
      <p>{{info.number}}</p>
    </div>
    <!--
    la partie cachée du dropdown: les donnés sont passées du App.vue et récupérées
    du json-server
    -->
    <Delivery
      :deliveryStatus="deliveryStatus"
    />
  </div>
</template>

<script>
import Delivery from './Delivery.vue'
export default {
  name: 'Purchase',
  props: {
    infoShopping: Array,
    deliveryStatus: Array,
  },
  components: {
    Delivery,
  },
}
</script>

<style scope>
.purchase-parent{
  width: 30vw;
  margin-top: 2rem;
  border-bottom: 1px solid;
  color: var(--tedicolor);
}
.purchase-info{
  display: flex;
  justify-content: space-between;
  width: 13vw;
}
.purchase-info p{
  font-size: 1.2rem;
  margin: .5rem 0;
}
.purchase-info p:last-of-type{
  font-weight: 700;
}
@media only screen and (max-width : 349px){
.purchase-info{
  width: 80%;
  }
.purchase-parent{
  width: 90vw;
  }
}
@media only screen and (min-width: 350px) and (max-width : 550px) {
.purchase-parent{
  width: 80%;
  margin-top: 10rem;
  }
.purchase-info{
  width: 90%;
  }
}
@media only screen and (min-width: 551px) and (max-width : 800px) {
.purchase-parent{
  width: 80%;
}
.purchase-info{
  width: 60%;
  }
}
@media only screen and (min-width: 801px) and (max-width : 1000px) {
.purchase-parent{
  width: 40%;
}
.purchase-info{
  width: 90%;
  }
}
@media only screen and (min-width: 1001px) and (max-width : 1400px) {
.purchase-parent{
  width: 40%;
}
.purchase-info{
  width: 65%;
  }
}
@media only screen and (min-width: 1401px) and (max-width : 1900px) {
.purchase-parent{
  width: 40%;
}
.purchase-info{
  width: 50%;
  }
}
</style>
