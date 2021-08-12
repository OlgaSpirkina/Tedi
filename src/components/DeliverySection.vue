<template>
  <div class="delivery_info_section">
    <div
      :delivery="delivery"
      :key="delivery.id"
      v-for="delivery in deliverySection"
      class="element_delivery">
      <h3>{{delivery.name.toUpperCase()}}</h3>
      <p
        :elem="elem"
        :key="elem.id"
        v-for="elem in delivery.info"
      >
        {{elem}}
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DeliverySection',
  props: {
    deliverySection: Array,
  },
  components: {

  },
}
</script>

<style scope>
.delivery_info_section{
  width: 70vw;
  height: 22vh;
  margin: 2rem auto;
  display: flex;
  justify-content: space-evenly;
  align-items: flex-start;
  color: var(--tedicolor);
  padding: .5rem;
  box-shadow: 2.5px 2.5px 5px 5px var(--verylightgrey);
}
.element_delivery{
  width: inherit;
  height: 15vh;
  border-right: 1px solid grey;
  padding: 1rem;
}
.element_delivery:last-child{
  border-right: none;
}
.element_delivery p{
  margin: 0;
  padding: 0;
}
.element_delivery h3{
  margin-top: 0;
}
@media only screen and (max-width : 590px) {
  .delivery_info_section{
    width: 90%;
    flex-direction: column;
    height: inherit;
  }
  .element_delivery{
    display: flex;
    flex-direction: column;
    justify-content: center;
    border-right: none;
    border-bottom: 1px solid grey;
    padding-bottom: 1rem;
  }
  .element_delivery div{
    margin-bottom: 1rem;
  }
  .element_delivery:last-child{
    border-bottom: none;
  }
}
@media only screen and (min-width : 591px) and (max-width : 699px) {
  .delivery_info_section{
    width: 95%;
    height: 25vh;
  }
  .element_delivery{
    padding: .5rem;
    height: 20vh;
  }
  .element_delivery div{
    margin-bottom: 1rem;
  }
}
@media only screen and (min-width : 700px) and (max-width : 1260px) {
  .delivery_info_section{
    width: 90%;
    height: 25vh;
  }
}


</style>
